# Curie Uniswap Arbitrage Strategy

When crypto markets start to trend upwards, the market participants tend to get leveraged long. This drives funding rates in perpetual futures up and the funding rate can remain positive for long periods of time. This means traders with short positions collect funding payments. Great! Free money. But what's the point of collecting funding if you're losing money holding a short position while the spot price runs against you?

You can create a neutral position by buying X amount of an asset in a spot market while simultaneously shorting X amount in the perpetual futures market. If price goes up, the profit in the spot market is cancelled by your loss in the perpetual futures market and vice versa. Now let's step back and paint a more detailed picture.

## The Markets

Both of these markets that will faciliate this strategy are deployed on [Optimism](https://www.optimism.io/), a low-cost and lightning-fast Ethereum L2 blockchain. This is nice because the funds used for the strategy can be controlled by the same wallet.

### Perpetual Protocol V2 (Curie)

[Perpetual Protocol V2](https://perp.com/) is a decentralized derivatives exchange donned with the name Curie after [Marie Curie](https://en.wikipedia.org/wiki/Marie_Curie). They offer up to 10x leverage on trading [perpetual futures](https://v2docs.perp.fi/quick-overview/more-about-perpetual-futures).

This is where the strategy will open a short position and earn [funding payments](https://v2docs.perp.fi/for-traders/funding-payments). 

### Uniswap

[Uniswap](https://uniswap.org/) is a decentralized crypto trading protocol. They are the most influential players in the decentralized finance space, and much of cryptoeconomies early levels of success are due to this innovative protocol.

This is where the strategy will open a long spot position to counterbalance the short perpetual futures position.

## Downside and Risk

The downside to this strategy is if the funding payment is consistently positive, that probably means the market is in a bull trend. So you have to consider the opportunity cost between deploying this strategy and just being fully allocated to a spot long position. Without any leverage, you need a 50-50 spot-futures split of your capital.

There is also the risk of the short perpetual futures position being [liquidated](https://v2docs.perp.fi/for-traders/liquidation). If your maintenance margin falls below 6.25% when calculated using the 15-minute TWAP of the index price, some or all of your margin will be taken as a penalty.

## Other Considerations

The strategy needs to take into account the cost of trading fees for Uniswap swaps and Curie perpetual futures trades. To reduce this overhead, the strategy should consider postions to be held on longer timeframes and rebalanced strategically.

The strategy operates better if it was automated. Manual execution could result in liquidation if the strategy isn't properly managed.

## Upside and Reward

This strategy lets you reduce the amount of risk and exposure to crypto markets by creating a neutral postion.

This strategy is passive and does not require much attention.

## Example of the Strategy in Action

1. Fund the strategy's wallet with $10_000 in stablecoins and enough OETH to cover transaction fees.

2. Select the asset the strategy will arbitrage.

3. Deposit $5_000 into Curie.

4. Wait for optimal conditions.

5. Purchase $5_000 of the asset in the spot market and simultaneously short the asset with $5_000 in the perpetual futures market.

6. Collect funding until the a trigger to close your position occurs.

7. Close your position.

8. Rebalance your spot allocation and perpetual futures allocation.

9. Return to step 4.

## Applying Leverage

To boost your return you can open a leveraged position, this results with less margin necessary in the perpetual futures allocation and allows you to have a bigger position. It also increases your risk of liquidation, but with proper risk management can be okay.

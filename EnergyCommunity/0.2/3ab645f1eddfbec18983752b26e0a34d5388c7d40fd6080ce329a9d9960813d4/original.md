split*yearly*financial*terms(ECModel::AbstractEC, profit*distribution)

Function to describe the cost term distributions by all users for all years.

## Parameters

  * ECModel : AbstractEC   EnergyCommunity model
  * profit_distribution   Final objective function
  * user*set*financial   User set to be considered for the financial analysis

## Returns

```
The output value is a NamedTuple with the following elements
- NPV: the NPV of each user given the final profit_distribution adjustment by game theory techniques
- CAPEX: the annualized CAPEX
- OPEX: the annualized operating costs (yearly maintenance and yearly peak and energy grid charges)
- REP: the annualized replacement costs
- RV: the annualized recovery charges
- REWARD: the annualized reward distribution by user
- PEAK: the annualized peak costs
- EN_SELL: the annualized revenues from energy sales
- EN_BUY: the annualized costs from energy consumption and buying
- EN_NET: the annualized net energy costs
```

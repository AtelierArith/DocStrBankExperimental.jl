```
business_plan(ECModel::AbstractEC, profit_distribution)
```

Function to describe the cost term distributions by all users for all years.

## Parameters

  * ECModel : AbstractEC   EnergyCommunity model
  * profit_distribution   Final objective function
  * user*set*financial   User set to be considered for the financial analysis

## Returns

```
The output value is a NamedTuple with the following elements
- df_business
    Dataframe with the business plan information
```

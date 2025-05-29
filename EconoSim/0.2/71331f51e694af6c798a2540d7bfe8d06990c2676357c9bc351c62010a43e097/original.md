```
process_sumsy!(balance::Balance, sumsy::SuMSy, step::Int)
```

Processes demurrage and guaranteed income if the timestamp is a multiple of the SuMSy interval. Otherwise this function does nothing. Returns the deposited guaranteed income amount and the subtracted demurrage. When this function is called with timestamp == 0, the balance will be 'seeded'. The seed amount is added to the returned income.

  * sumsy: the SuMSy implementation to use for calculations.
  * balance: the balance on which to apply SuMSy.
  * timestamp: the current timestamp. Used to determine whether action needs to be taken.

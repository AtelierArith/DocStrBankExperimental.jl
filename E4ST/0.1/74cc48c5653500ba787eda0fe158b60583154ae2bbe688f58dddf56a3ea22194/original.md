```
setup_welfare!(config, data)
```

Sets up the welfare structure.  Add in welfare terms for our standard welfare results and for several welfare checks.

Welfare Checks: 

  * `system_cost_check` - This is the "system cost" and the delta of total system cost should equal the delta of the sum of user, producer, and government revenue.
  * `electricity_payments` - This should sum to zero to check whether electricity payments equals electricity revenue paid to producers.
  * `net_rev_prelim_check` - This is meant to check that producer `net_total_revenue_prelim` is being calculated correctly, particularly when there are reserve requirements. The sum of this check should equal the sum of `net_total_revenue_prelim` for gen and storage.

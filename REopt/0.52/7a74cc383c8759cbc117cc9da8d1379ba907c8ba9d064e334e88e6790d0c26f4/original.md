```
BAUScenario(s::Scenario)
```

Constructs the BAUScenario (used to create the Business-as-usual inputs) based on the Scenario for the optimized case.

The following assumptions are made for the BAU scenario: 

  * sets the `PV` and `Generator` min*kw and max*kw values to the existing_kw values
  * sets wind and storage max_kw values to zero (existing wind and storage cannot be modeled)

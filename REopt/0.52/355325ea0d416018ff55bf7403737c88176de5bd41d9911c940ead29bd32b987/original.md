```
easiur_data(; latitude::Real, longitude::Real, inflation::Real)
```

This function gets NOx, SO2, and PM2.5 costs (for grid and on-site emissions) and cost escalation rates from the EASIUR dataset.

This function is used for the /easiur_costs endpoint in the REopt API, in particular      for the webtool to display health emissions cost/escalation defaults before running REopt,      but is also generally an external way to access EASIUR data without running REopt.

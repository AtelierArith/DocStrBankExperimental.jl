```
parse_lmp_results!(config, data, res_raw)
```

Adds the locational marginal prices of electricity and power flow.

| table_name | col_name    | unit                | description                                |
|:---------- |:----------- |:------------------- |:------------------------------------------ |
| :bus       | :lmp_elserv | DollarsPerMWhServed | Locational Marginal Price of Energy Served |
| :branch    | :lmp_pflow  | DollarsPerMWFlow    | Locational Marginal Price of Power Flow    |

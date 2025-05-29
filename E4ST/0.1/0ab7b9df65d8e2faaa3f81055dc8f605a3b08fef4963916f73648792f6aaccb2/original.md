```
constrain_pbal!(config, data, model) -> nothing
```

Constrain the power balancing equation to equal zero for each bus, at each year and hour.

Depending on `config[:line_loss_type]`, the power balancing equation can be implemented in 2 ways:

  * `pflow`:  `plgen_bus - plserv_bus + pflow_in_bus * (1 - line_loss_rate) - pflow_out_bus == 0`
  * `plserv`:  `plgen_bus - plserv_bus / (1 - line_loss_rate) - pflow_bus == 0`

Where:

  * `pgen_bus` is the power generated at the bus
  * `plserv_bus` is the power served/consumed at the bus
  * `pflow_bus` is the net power flowing out of the bus (positive or negative)
  * `pflow_in_bus` is the (positive) power flowing into the bus
  * `pflow_out_bus` is the (positive) power flowing out of the bus

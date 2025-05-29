```
modify_model!(mod::InterfaceLimit, config, data, model)
```

  * Gathers each of the branches (forward and reverse) for each of the rows of the `interface_limit` table.
  * Creates an expression `pflow_if[if_idx, yr_idx, hr_idx]` for the power flowing, in MW, in each interface.  This includes

      * The sum of all of the `pflow_branch` terms for branches that are flowing in the direction of **f**rom to **t**o.
      * Net the sum of all of the `pflow_branch` terms for branches that are flowing in the direction of **t**o to **f**rom.
  * Creates min and max constraints `cons_pflow_if_min[if_idx, yr_idx, hr_idx]` and `cons_pflow_if_max[if_idx, yr_idx, hr_idx]` for each interface limit, for each year and hour in which the limit is finite, and there are qualifying `pflow_branch` variables in the interface.
  * Creates min and max constraints `cons_eflow_if_min[if_idx, yr_idx]` and `cons_eflow_if_max[if_idx, yr_idx]` for each interface limit, for each year in which the limit is finite, and there are qualifying `pflow_branch` variables in the interface.
  * Creates expression `interface_flow_cost_obj[if_idx, yr_idx, hr_idx]` for the cost of interface flow, and adds it to the objective.

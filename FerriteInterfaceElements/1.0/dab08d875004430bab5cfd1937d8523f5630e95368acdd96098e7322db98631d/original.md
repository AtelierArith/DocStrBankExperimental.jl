```
insert_interfaces(grid, domain_names; topology=ExclusiveTopology(grid))
```

Return a new grid with `InterfaceCell`s inserted betweenthe domains defined by `domain_names`. The new grid provides additional cell sets. The set `"interfaces"` contains all new `InterfaceCell`s and two sets are provided for each combination of domain names: `"domain1-domain2-inertface"` and  `"domain2-domain1-inertface"` both using the same `Set`.

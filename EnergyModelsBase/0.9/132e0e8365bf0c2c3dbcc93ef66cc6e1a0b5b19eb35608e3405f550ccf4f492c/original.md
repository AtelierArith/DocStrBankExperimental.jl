```
has_emissions(l::Link)
```

Checks whether link `l` has emissions.

By default, links do not have emissions. You must dispatch on this function if you want to introduce links with associated emissions, *e.g.*, through leakage.

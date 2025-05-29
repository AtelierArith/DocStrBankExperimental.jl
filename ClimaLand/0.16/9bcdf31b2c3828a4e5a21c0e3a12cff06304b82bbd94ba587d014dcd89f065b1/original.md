```
total_liq_water_vol_per_area!(cache, model::AbstractModel, Y, p, t)
```

A function which updates `cache` in place with the total liquid water volume per unit ground area for the `model`, computed from `Y`, `p`, and `t`.

While water mass is the fundamentally conserved quantity, soil modelling represents water by an equivalent water volume using the density of water and ice at standard temperature and pressure. Because of that, we report here the total volume of water present in a model (per unit area) that would arise if all the water was in liquid phase. This can be converted to a mass using the density of liquid water.

This includes the water in multiple phases. For example, if ice is present, the water volume is computed using ratio of the density of ice to the density of liquid water.

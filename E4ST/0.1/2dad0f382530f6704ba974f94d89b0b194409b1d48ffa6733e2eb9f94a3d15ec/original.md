```
setup_table!(config, data, ::Val{:af_table})
```

Populates the `af` column of the `gen_table`.  

Updates the generator table with the availability factors provided.  By default assigns an availability factor of `1.0` for every generator.  See [`summarize_table(::Val{:af_table})`](@ref).

Often, generators are unable to generate energy at their nameplate capacity over the course of any given representative hour.  This could depend on any number of things, such as how windy it is during a given representative hour, the time of year, the age of the generating unit, etc.  The ratio of available generation capacity to nameplate generation capacity is referred to as the availability factor (AF).

The availability factor table includes availability factors for groups of generators specified by any combination of area, genfuel, gentype, year, and hour.

$$
P_{G_{g,h,y}} \leq f_{\text{avail}_{g,h,y}} \cdot P_{C{g,y}} \qquad \forall \{g \in \text{generators}, h \in \text{hours}, y \in \text{years} \}
$$

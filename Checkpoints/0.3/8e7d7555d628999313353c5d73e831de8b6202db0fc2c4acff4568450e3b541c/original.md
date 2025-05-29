```
tags(x::IndexEntry)
```

All tags and there values of the checkpoint. This is a collection of pairs. For example if the checkpoint was saved using:

```julia
with_tag(:sim_now=>DateTime(2000,1,1,9,00), grid=ERCOT) do
    checkpoint(Forecasters, "forecasts", ...)`
end
```

Then `tags(x)` would return: `(:sim_now="2000-01-01T09:00:00", :grid=>"ERCOT")`.

Note that if the tags are unique, then their values call also be accessed via a `getproperty` overload, e.g as `x.sim_now` or `x.grid`.

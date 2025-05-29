```
Label(lbl::Symbol) :: Query
```

This assigns a label to the output.

```jldoctest
julia> unitknot[Lift("Hello World") >> Label(:greeting)]
│ greeting    │
┼─────────────┼
│ Hello World │
```

A label could also be assigned using the `=>` operator.

```jldoctest
julia> unitknot[:greeting => Lift("Hello World")]
│ greeting    │
┼─────────────┼
│ Hello World │
```

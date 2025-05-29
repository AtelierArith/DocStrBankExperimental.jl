```
stripunits(model::AbstractModel, xs)
stripunits(param::AbstractParam, x)
```

Returns the `x` or `xs` divided by their corresponding units field, if it exists.

It there is no units field, and x has units, it will be returned with units! It you want to simply remove all units, using Unitful.ustrip.

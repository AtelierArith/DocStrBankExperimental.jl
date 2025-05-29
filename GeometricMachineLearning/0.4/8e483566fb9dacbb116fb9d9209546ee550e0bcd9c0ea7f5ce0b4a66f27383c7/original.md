```
DataLoader(data::QPT)
```

Make an instance of `DataLoader` based on $(q, p)$ data.

# Implementation

In this case the field `input_dim` of `DataLoader` is interpreted as the sum of the $q$- and $p$-dimensions, i.e. if $q$ and $p$ both evolve on $\mathbb{R}^n$, then `input_dim` is $2n$.

Apart from this the input is treated similarly as if it were an `Array`, i.e. everything is converted to tensors internally. See e.g. [`DataLoader{::AbstractArray{<:Number, 3}}`](@ref).

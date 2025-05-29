```
project!(x::AbstractArray{<:Real,N},bc::BoundConstraints{<:Real,N})
```

Project `x` such that $x \in [l,u]$ is fullfiled.

See: [`BoundConstraints`](@ref) 

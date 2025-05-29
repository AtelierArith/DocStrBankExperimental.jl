```
project!(x::AbstractArray{<:Real,N},bc::BoundConstraints{<:Real,N})
```

`x`をプロジェクトして、$x \in [l,u]$が満たされるようにします。

参照: [`BoundConstraints`](@ref) 

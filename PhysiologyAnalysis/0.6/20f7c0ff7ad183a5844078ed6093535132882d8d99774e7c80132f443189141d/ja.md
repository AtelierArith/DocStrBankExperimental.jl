```
function IRfit(intensity::AbstractArray{T}, response::AbstractArray{T};
    lb::AbstractArray{T} = [1.0, 1.0, 0.1], #デフォルト rmin = 100, kmin = 0.1, nmin = 0.1 
    p0::AbstractArray{T} = [500.0, 1000.0, 2.0], #デフォルト r = 500.0, k = 200.0, n = 2.0
    ub::AbstractArray{T} = [Inf, Inf, 10.0], #デフォルト rmax = 2400, kmax = 800
) where {T<:Real}
```

この関数はXおよびYの値を取り、HILLタイプのフィットに従ってフィッティングします。

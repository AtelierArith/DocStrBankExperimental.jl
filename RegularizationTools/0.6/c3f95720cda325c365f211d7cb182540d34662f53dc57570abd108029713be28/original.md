```
forwardmodel(
    s::AbstractVector{T1},
    x::AbstractVector{T2},
    f::Function,
)::AbstractArray where {T1<:Any,T2<:Number}
```

Forward model that maps numerical values [x] corresponding to  setpoints [s] to output [y], given the function f. The function f must  accept a single argument of type [Domain](@ref) and provide a  numerical mapping between input $x$ and output $y$ at query point $q$.

Note that the [designmatrix](@ref) and forward model are related

```
A = designmatrix(s, q, f)
y1 = A*x

y2 = forwardmodel(s, x, q, f)
y1 == y2
```

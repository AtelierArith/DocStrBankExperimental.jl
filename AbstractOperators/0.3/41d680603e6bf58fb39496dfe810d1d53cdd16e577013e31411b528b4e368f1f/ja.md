`is_sliced(A::AbstractOperator)`

`A`がスライスされたオペレーターであるかどうかをテストします。

```julia
julia> is_sliced(GetIndex((10,), 1:5))
true

```

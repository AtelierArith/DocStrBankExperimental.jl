```julia
group!(f::Function, c::AbstractContext, name::String, w::Int64 = c.dim[1],
    h::Int64 = c.dim[2], margin::Pair{Int64, Int64} = c.margin) -> ::Nothing
```

`name`という名前のレイヤーを`c`上に作成し、そのレイヤーを提供された次元にスケーリングします。

```example

```

```
a - b
a - 2
```

`a-b` の `Int` | `Real` 表現を返します（`a-b` の型を継承します）。ベクトル値および行列値の式にはドットブロードキャスティングを使用します。

```julia
@satvariable(a[1:n], Int)
@satvariable(b[1:n, 1:m], Int)
a .- b
println("typeof a-b: $(typeof(a[1] - b[1]))")

@satvariable(c, Real)
println("typeof a-c: $(typeof(a[1] - c))")

@satvariable(z, Bool)
a .- z
println("typeof a-z: $(typeof(a[1] - z))")
```

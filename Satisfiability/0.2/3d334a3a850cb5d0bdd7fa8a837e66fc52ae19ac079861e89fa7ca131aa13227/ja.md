```
a + b
a + 1 + true
```

`Int` | `Real` 表現 `a+b` を返します（`a+b` の型を継承します）。ベクトル値および行列値の表現にはドットブロードキャスティングを使用します。

```julia
@satvariable(a[1:n], Int)
@satvariable(b[1:n, 1:m], Int)
a .+ b
println("typeof a+b: $(typeof(a[1] + b[1]))")

@satvariable(c, Real)
println("typeof a+c: $(typeof(a[1] + c))")

@satvariable(z, Bool)
a .+ z
println("typeof a+z: $(typeof(a[1] + z))")
```

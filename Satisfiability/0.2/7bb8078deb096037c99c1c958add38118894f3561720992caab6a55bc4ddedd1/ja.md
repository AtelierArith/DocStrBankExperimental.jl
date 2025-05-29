```
a / b
a / 2.0
```

`a/b` の `Real` 除算式を返します。注意: `a` と `b` は `RealExpr` に変換されます。ベクトル値および行列値の式にはドットブロードキャスティングを使用してください。

```julia
@satvariable(a[1:n], Real)
@satvariable(b[1:n, 1:m], Real)
a ./ b
println("typeof a/b: $(typeof(a[1]/b[1]))")
```

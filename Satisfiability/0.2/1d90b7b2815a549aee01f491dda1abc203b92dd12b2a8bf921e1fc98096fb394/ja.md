```
div(a, b)
div(a, 2)
```

`div(a,b)` の `Int` 除算式を返します。注意: `a` と `b` は `IntExpr` に変換されます。ベクトル値および行列値の式にはドットブロードキャスティングを使用してください。

```julia
@satvariable(a[1:n], Int)
@satvariable(b[1:n, 1:m], Int)
div.(a, b)
println("typeof div(a,b): $(typeof(div(a[1],b[1])))")
```

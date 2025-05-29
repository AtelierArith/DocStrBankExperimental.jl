```
@expression(args...)
```

効率的に線形または二次の式を構築しますが、モデルに即座に追加することはありません。代わりに、他の制約に挿入できる式を返します。例えば：

```julia
@expression(m, shared, sum(i*x[i] for i=1:5))
@constraint(m, shared + y >= 5)
@constraint(m, shared + z <= 10)
```

`ref`は`@variable`と同様にインデックスセットを受け入れ、そのインデックスは式の構築に使用できます：

```julia
@expression(m, expr[i=1:3], i*sum(x[j] for j=1:3))
```

匿名構文もサポートされています：

```julia
expr = @expression(m, [i=1:3], i*sum(x[j] for j=1:3))
```

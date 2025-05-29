```
reversecholesky!(A::AbstractMatrix, NoPivot(); check = true) -> ReverseCholesky
```

[`reversecholesky`](@ref) と同じですが、コピーを作成するのではなく、入力 `A` を上書きすることでスペースを節約します。因子分解が `A` の要素型で表現できない数を生成した場合、例えば整数型の場合、[`InexactError`](@ref) 例外がスローされます。```

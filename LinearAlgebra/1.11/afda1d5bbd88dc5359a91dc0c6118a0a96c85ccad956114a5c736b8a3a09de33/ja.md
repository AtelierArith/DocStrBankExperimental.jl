```
cholesky!(A::AbstractMatrix, NoPivot(); check = true) -> Cholesky
```

[`cholesky`](@ref) と同じですが、入力 `A` を上書きすることでスペースを節約します。コピーを作成するのではなく、[`InexactError`](@ref) 例外は、因子分解が `A` の要素型で表現できない数を生成した場合にスローされます。例えば、整数型の場合です。

# 例

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> cholesky!(A)
ERROR: InexactError: Int64(6.782329983125268)
Stacktrace:
[...]
```

```julia
DiagonalOperator(
    diag;
    update_func,
    update_func!,
    accepted_kwargs
)

```

`AbstractVecOrMat` に適用できる要素ごとのスケーリング（対角スケーリング）操作を表します。`diag` が長さ N の `AbstractVector` の場合、`L = DiagonalOperator(diag, ...)` は `size(u, 1) == N` の `AbstractArray` に適用できます。`v` の各列は `diag` によってスケーリングされ、`LinearAlgebra.Diagonal(diag) * v` のようになります。

`diag` が多次元配列の場合、`L = DiagonalOperator(diag, ...)` はサイズ `(N, N)` の演算子を形成し、ここで `N = size(diag, 1)` は `diag` の先頭の長さです。`L` は、先頭の長さ `size(u, 1) = N` を持つ `length(v) = length(diag)` の配列に対する要素ごとのスケーリング操作です。

その状態は、演算子評価中にユーザー提供の `update_func` によって更新されます（`L([w,], v, u, p, t)`）、または `update_coefficients[!](L, u, p, t)` への呼び出しによって更新されます。どちらも `update_function`、`update_func` を再帰的に呼び出し、次のシグネチャを持つと仮定されます。

```
update_func(diag::AbstractVecOrMat, u, p, t; <accepted kwargs>) -> new_diag
```

または

```
update_func!(diag::AbstractVecOrMat, u, p, t; <accepted kwargs>) -> [modifies diag]
```

`update_func[!]` によって受け入れられるキーワード引数のセットは、`accepted_kwargs` というキーワード引数を介して `MatrixOperator` に `Symbol` のタプルとして提供されなければなりません。`accepted_kwargs` が提供されていない場合、`kwargs` は `update_func[!]` に渡すことができません。

!!! warning
    ユーザー提供の `update_func[!]` は、その計算に `u` を使用してはなりません。`update_func[!]` への位置引数 `(u, p, t)` は、`update_coefficients[!](L, u, p, t)` によって渡され、ここで `u` は合成 `AbstractSciMLOperator` への入力ベクトルです。そのため、`u` の値や形状は、`update_func[!]` が期待する入力に対応しない可能性があります。演算子の状態がその入力ベクトルに依存する場合、それは定義上、非線形演算子です。このような非線形性は `FunctionOperator` に保持することをお勧めします。このトピックは（この問題）[https://github.com/SciML/SciMLOperators.jl/issues/159] でさらに議論されています。


# 例

```
@marginalrule NodeType(:Cluster) (Arguments..., [ meta::MetaType ]) = begin
    # ルール本体
    return ...
end
```

`@marginalrule` マクロは、`marginalrule` 関数の新しいメソッドを定義するのに役立ちます。これは特に `@node` マクロと組み合わせてうまく機能します。特定の構造を持ち、次のことを指定する必要があります：

  * `NodeType`: 有効な Julia 型でなければなりません。Julia 関数（例えば `+`）のルールを定義しようとする場合は、`typeof(+)` を使用します。
  * `Cluster`: `_` シンボルで結合されたエッジラベルを含むエッジクラスタ。通常、エッジラベルは `@node` マクロで定義されます。
  * `Arguments`: ルールの入力引数のリストを定義します。

      * `m_*` プレフィックスは、引数がエッジ `*` からの `Message` 型であることを示します。
      * `q_*` プレフィックスは、引数がエッジ `*` 上の `Marginal` 型であることを示します。
  * `Meta::MetaType` - オプションで、ユーザーは `MetaType` 型の `Meta` オブジェクトを指定できます。これは、異なる近似手法で異なるルールを試みる場合や、ルール自体が一時的なストレージやキャッシュを必要とする場合に便利です。デフォルトのメタは `nothing` です。

`@marginalrule` は、`return` ステートメントで `NamedTuple` を返すことができます。これは、`Cluster` の結合周辺のいくつかの変数が独立しており、結合自体が因子分解されていることを示します。例えば、`q(x, y)` の周辺を計算しようとする場合、計算の結果として `(x = ..., y = ...)` を返すことが可能であり、これは `q(x, y) = q(x)q(y)` を示します。

以下は、`@marginalrule` マクロの使用例です：

1. `q(out, μ)` のための `NormalMeanPrecision` ノード周辺の周辺計算ルール。このルールは、`out` および `μ` エッジからのメッセージである `m_out` と `m_μ` の引数を受け入れ、エッジ `τ` 上の周辺である `q_τ` を受け入れます。

```julia
@marginalrule NormalMeanPrecision(:out_μ) (m_out::UnivariateNormalDistributionsFamily, m_μ::UnivariateNormalDistributionsFamily, q_τ::Any) = begin
    xi_out, W_out = weightedmean_precision(m_out)
    xi_μ, W_μ     = weightedmean_precision(m_μ)

    W_bar = mean(q_τ)

    W  = [W_out+W_bar -W_bar; -W_bar W_μ+W_bar]
    xi = [xi_out; xi_μ]

    return MvNormalWeightedMeanPrecision(xi, W)
end
```

2. `q(out, μ)` のための `NormalMeanPrecision` ノード周辺の周辺計算ルール。このルールは、`out` および `μ` エッジからのメッセージである `m_out` と `m_μ` の引数を受け入れ、エッジ `τ` 上の周辺である `q_τ` を受け入れます。この例では、計算の結果は `NamedTuple` です。

```julia
@marginalrule NormalMeanPrecision(:out_μ) (m_out::PointMass, m_μ::UnivariateNormalDistributionsFamily, q_τ::Any) = begin
    return (out = m_out, μ = prod(ClosedProd(), NormalMeanPrecision(mean(m_out), mean(q_τ)), m_μ))
end
```

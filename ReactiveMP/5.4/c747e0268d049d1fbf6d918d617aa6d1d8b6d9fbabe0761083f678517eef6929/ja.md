```
@rule NodeType(:Edge, Constraint) (Arguments..., [ meta::MetaType ]) = begin
    # ルール本体
    return ...
end
```

`@rule` マクロは `rule` 関数の新しいメソッドを定義するのに役立ちます。特に `@node` マクロと組み合わせてうまく機能します。特定の構造を持ち、次のことを指定する必要があります：

  * `NodeType`: 有効な Julia 型でなければなりません。Julia 関数（例えば `+`）のルールを定義しようとする場合は、`typeof(+)` を使用してください。
  * `Edge`: エッジラベルで、通常エッジラベルは `@node` マクロで定義されます。
  * `Constrain`: 非推奨、単に `Marginalisation` ラベルを使用してください。
  * `Arguments`: ルールの入力引数のリストを定義します。

      * `m_*` プレフィックスは、引数がエッジ `*` からの `Message` 型であることを示します。
      * `q_*` プレフィックスは、引数がエッジ `*` の `Marginal` 型であることを示します。
  * `Meta::MetaType` - オプションで、ユーザーは `MetaType` 型の `Meta` オブジェクトを指定できます。これは、異なる近似手法で異なるルールを試みる場合や、ルール自体が一時的なストレージやキャッシュを必要とする場合に便利です。デフォルトのメタは `nothing` です。

以下は `@rule` マクロの使用例です：

1. `NormalMeanVariance` ノードに対する `:μ` エッジの `Marginalisation` 制約を持つ信念伝播（または和-積）メッセージ更新ルール。入力引数は `m_out` と `m_v` で、対応するエッジ `out` と `v` からのメッセージで、型は `PointMass` です。

```julia
@rule NormalMeanVariance(:μ, Marginalisation) (m_out::PointMass, m_v::PointMass) = NormalMeanVariance(mean(m_out), mean(m_v))
```

2. `NormalMeanVariance` ノードに対する `:μ` エッジの `Marginalisation` 制約を持つ平均場メッセージ更新ルール。入力引数は `q_out` と `q_v` で、対応するエッジ `out` と `v` の型は `Any` の周辺分布です。

```julia
@rule NormalMeanVariance(:μ, Marginalisation) (q_out::Any, q_v::Any) = NormalMeanVariance(mean(q_out), mean(q_v))
```

3. `NormalMeanVariance` ノードに対する `:out` エッジの `Marginalisation` 制約を持つ構造化変分メッセージ更新ルール。入力引数は `m_μ` で、型は `UnivariateNormalDistributionsFamily` の `μ` エッジからのメッセージであり、`q_v` は型 `Any` の `v` エッジの周辺分布です。

```julia
@rule NormalMeanVariance(:out, Marginalisation) (m_μ::UnivariateNormalDistributionsFamily, q_v::Any) = begin
    m_μ_mean, m_μ_cov = mean_cov(m_μ)
    return NormalMeanVariance(m_μ_mean, m_μ_cov + mean(q_v))
end
```

参照： [`rule`](@ref), [`marginalrule`](@ref), [`@marginalrule`], [`@call_rule`](@ref)

```
ManifoldCachedObjective{E,P,O<:AbstractManifoldObjective{<:E},C<:NamedTuple{}} <: AbstractDecoratedManifoldObjective{E,P}
```

`NamedTuple`に基づいて目的関数のキャッシュを作成します。この`NamedTuple`は、何らかのキャッシュを格納します。

# コンストラクタ

```
ManifoldCachedObjective(M, o::AbstractManifoldObjective, caches::Vector{Symbol}; kwargs...)
```

[`AbstractManifoldObjective`](@ref)のキャッシュを作成します。`caches`内のシンボルは、どの関数評価をキャッシュするかを示します。

# サポートされているシンボル

| シンボル                        | キャッシュする呼び出し (含む `!` バリアント)                     | コメント          |
|:--------------------------- |:---------------------------------------------- |:------------- |
| `:Cost`                     | [`get_cost`](@ref)                             |               |
| `:EqualityConstraint`       | [`get_equality_constraint`](@ref)`(M, p, i)`   |               |
| `:EqualityConstraints`      | [`get_equality_constraint`](@ref)`(M, p, :)`   |               |
| `:GradEqualityConstraint`   | [`get_grad_equality_constraint`](@ref)         | (p,i)ごとの接ベクトル |
| `:GradInequalityConstraint` | [`get_inequality_constraint`](@ref)            | (p,i)ごとの接ベクトル |
| `:Gradient`                 | [`get_gradient`](@ref)`(M,p)`                  | 接ベクトル         |
| `:Hessian`                  | [`get_hessian`](@ref)                          | 接ベクトル         |
| `:InequalityConstraint`     | [`get_inequality_constraint`](@ref)`(M, p, j)` |               |
| `:InequalityConstraints`    | [`get_inequality_constraint`](@ref)`(M, p, :)` |               |
| `:Preconditioner`           | [`get_preconditioner`](@ref)                   | 接ベクトル         |
| `:ProximalMap`              | [`get_proximal_map`](@ref)                     | `(p,λ,i)`ごとの点 |
| `:StochasticGradients`      | [`get_gradients`](@ref)                        | 接ベクトルのベクトル    |
| `:StochasticGradient`       | [`get_gradient`](@ref)`(M, p, i)`              | (p,i)ごとの接ベクトル |
| `:SubGradient`              | [`get_subgradient`](@ref)                      | 接ベクトル         |
| `:SubtrahendGradient`       | [`get_subtrahend_gradient`](@ref)              | 接ベクトル         |

# キーワード引数

  * `p`:           (`rand(M)`) キャッシュに使用されるキーの型。デフォルトは`M`のデフォルト表現です。
  * `value`:       (`get_cost(M, objective, p)`) キャッシュ内の数値値の型
  * `X`:           (`zero_vector(M,p)`) 勾配およびヘッセ行列呼び出しのためにキャッシュされる値の型。
  * `cache`:       (`[:Cost]`) どの関数呼び出しをキャッシュすべきかを示すシンボルのベクトル。
  * `cache_size`:  (`10`) キャッシュする呼び出しの数 (最も最近使用されていない)
  * `cache_sizes`: (`Dict{Symbol,Int}()`) 各キャッシュのサイズを個別に指定する名前付きタプルまたは辞書。

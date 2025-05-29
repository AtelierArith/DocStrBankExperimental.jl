```
DiscreteMeasureData{P <: Union{JuMP.AbstractVariableRef,
                    Vector{<:JuMP.AbstractVariableRef}},
                    N, B <: Union{Float64, Vector{Float64}},
                    F <: Function
                    } <: AbstractMeasureData
```

不変測度抽象データのためのデータ型で、抽象は次の形式です: $measure = \int_{\tau \in T} f(\tau) w(\tau) d\tau \approx \sum_{i = 1}^N \alpha_i f(\tau_i) w(\tau_i)$。サポートと係数は不変であり（つまり、基礎となる無限パラメータのためにサポートが変更されても変わりません）、この型は1次元および多次元の測度の両方に使用できます。

**フィールド**

  * `parameter_refs::P`: 積分が行われる無限のパラメータ。これらは複数の独立したパラメータで構成できますが、依存パラメータは他のタイプと混合できません。
  * `coefficients::Vector{Float64}`: 上記の測度抽象のための係数 $\alpha_i$。
  * `supports::Array{Float64, N}`: サポートポイント $\tau_i$。これは、1つのパラメータのみが与えられた場合は `Vector` であり、そうでない場合はサポートが列ごとに格納される `Matrix` です。
  * `label::DataType`: 無限のパラメータに格納されるサポートポイント $\tau_i$ のラベルで、[`AbstractSupportLabel`](@ref) に由来します。
  * `weight_function::F`: 重み付け関数 $w$ は、個々のサポート値を `Real` スカラー値にマッピングする必要があります。
  * `lower_bounds::B`: $T$ に従った下限で、これは測度の意図された区間を示し、無視される場合は `NaN` であるべきです。
  * `upper_bounds::B`: 上記と同様ですが、上限です。
  * `is_expect::Bool`: このデータは期待値呼び出しに関連していますか？

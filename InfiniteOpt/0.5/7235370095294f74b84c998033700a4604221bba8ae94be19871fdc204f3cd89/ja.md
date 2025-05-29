```
FunctionalDiscreteMeasureData{P <: Union{JuMP.AbstractVariableRef,
                              Vector{<:JuMP.AbstractVariableRef}},
                              B <: Union{Float64, Vector{Float64}},
                              I <: AbstractGenerativeInfo,
                              F1 <: Function,
                              F2 <: Function
                              } <: AbstractMeasureData
```

可変測度抽象データのためのデータ型で、抽象は次の形式です：$measure = \int_{\tau \in T} f(\tau) w(\tau) d\tau \approx \sum_{i = 1}^N \alpha_i f(\tau_i) w(\tau_i)$。この抽象は[`DiscreteMeasureData`](@ref)のものと同等ですが、測度作成時にサポートが完全には知られていないという違いがあります。したがって、測度が評価（展開）されるときに具体的なサポートポイント$\tau_i$とその係数$\alpha_i$を生成するために使用される関数が保存されます。これらのサポートは、`label`に従って特定され/生成され、少なくとも`num_supports`が生成されることが保証されます。たとえば、`label = MCSample`で`num_supports = 100`の場合、測度は`MCSample`というラベルの`parameter_refs`に保存されているすべてのサポートを使用し、少なくとも100が生成されることを保証します。このタイプは1次元および多次元の測度の両方に使用できます。

独立した無限パラメータに対する1次元測度の場合、`generative_supp_info`は、`label`を持つ既存のものに基づいて生成的サポートを作成するために必要な情報を指定します。無限パラメータごとに1種類の生成的サポートのみが許可されることに注意してください。

**フィールド**

  * `parameter_refs::P`: 積分が行われる無限パラメータ。これらは複数の独立したパラメータで構成できますが、依存パラメータは他のタイプと混在させることはできません。
  * `coeff_function::F1`: 上記の測度抽象のための$\alpha_i$を生成する係数生成関数。すべてのサポートを入力（配列としてフォーマット）として受け取り、対応する係数ベクトルを返す必要があります。
  * `min_num_supports::Int`: `parameter_refs`および`label`に関連して望ましいサポート$\tau_i$の最小数を指定します。
  * `label::DataType`: 無限パラメータに保存される/されるサポートポイント$\tau_i$のラベルで、[`AbstractSupportLabel`](@ref)から派生します。
  * `generative_supp_info::I`: 他の既存のものに基づいてサポートを生成するために必要な情報。
  * `weight_function::F2`: 重み付け関数$w$は、個々のサポート値を`Real`スカラー値にマッピングする必要があります。
  * `lower_bounds::B`: $T$に従った下限、これは測度の意図された区間を示し、無視される場合は`NaN`であるべきです。
  * `upper_bounds::B`: 上記と同様ですが、上限です。
  * `is_expect::Bool`: このデータは期待値呼び出しに関連していますか？

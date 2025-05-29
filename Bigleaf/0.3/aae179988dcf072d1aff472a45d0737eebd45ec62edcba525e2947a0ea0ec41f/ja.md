```
compute_Gb!(df::AbstractDataFrame, approach; kwargs...)
```

境界層伝導率を推定します。

# 引数

  * `df`       : 必要な変数を含むDataFrame（アプローチに依存）
  * `approach` : 次のいずれか

      * `Thom1972()`: [`Gb_Thom`](@ref)を参照
      * `Choudhury1988()`: [`Gb_Choudhury`](@ref)を参照
      * `Su2001()`: [`Gb_Su`](@ref)を参照
      * `ConstantKB1()`: [`Gb_constant_kB1`](@ref)を参照

異なるアプローチには、`df`に存在する必要がある異なる変数と異なるキーワード引数が必要です。

# 値

以下の列を持つ更新されたDataFrame `df`:

  * `Gb_h`: 熱伝達のための境界層伝導率 (m s-1)

その後の導出量については、次を参照してください

  * [`compute_Gb_quantities`](@ref)は抵抗、kB^(-1)定数、およびCO2伝導率について
  * [`add_Gb!`](@ref)はシュミット数が与えられた他の種の伝導率について

# 参照

[`Gb_Thom`](@ref), [`Gb_Choudhury`](@ref), [`Gb_Su`](@ref), [`Gb_constant_kB1`](@ref),  [`aerodynamic_conductance!`](@ref)

```jldoctest; output = false
using DataFrames
df = DataFrame(wind=[3,4,5], ustar=[0.5,0.6,0.65]) 
compute_Gb!(df, Thom1972())
≈(df.Gb_h[1], 0.102, rtol=1e-2)
# output
true
```

```
add_Ga(Gb_h, Ga_m, Sc::Vararg{Pair,N}; constants)
add_Ga!(df::AbstractDataFrame, Sc; Gb_h = df.Gb_h, Ga_m = df.Ga.m, kwargs...)
```

与えられたシュミット数に対する追加の空力伝導量を計算します

# 引数

  * `Gb_h`     : 熱伝達のための境界層伝導率 (m s-1)
  * `Ga_m`     : 運動量のための空力伝導率 (m s-1)
  * `Sc`       : 計算される追加の伝導率の出力名とシュミット数を含む複数の `Pair{Symbol,Number}`
  * `df`       : 出力列を追加するためのDataFrame

オプション

  * `constants=`[`BigleafConstants`](@ref)`()`: エントリを持つ辞書 

      * `Pr` - プラントル数

# 詳細

空力伝導率は次のように計算されます

$$
G_{a_x} = 1/(1/G_{a_m} + 1/G_{b_x})
$$

ここで `Gb_x` は他の量 x のための境界層伝導率であり、熱伝達のための境界層、シュミット数、およびプラントル数に基づいて計算されます。これは [`add_Gb!`](@ref) に文書化されています。

# 値

`Ga_x` というキーを持つ NameTuple または `df` で、ここで `x` は `Sc` のキーであり、対応する空力伝導率 (m s-1) です。

# 例

```jldoctest; output=false
using DataFrames
df = DataFrame(Gb_h=[0.02, missing, 0.055], Ga_m = 1 ./ [0.03, 0.03, 0.03])
add_Ga!(df, :O2 => 0.84, :CH4 => 0.99)
propertynames(df)[3:4] == [:Ga_O2, :Ga_CH4]
# output
true
```

```
add_Gb(Gb_h::Union{Missing,Number}, Sc::Vararg{Pair,N}; constants)
add_Gb!(df::AbstractDataFrame, Sc::Vararg{Pair,N}; Gb_h = df.Gb_h, kwargs...)
```

与えられたシュミット数に対する追加の量の境界層伝導率を計算します

# 引数

  * `Gb_h`     : 熱伝達のための境界層伝導率 (m s-1)
  * `Sc`       : 計算される追加の伝導率の出力名とシュミット数を含む複数の `Pair{Symbol,Number}`
  * `df`       : 出力列を追加するためのDataFrame

オプション

  * `constants=`[`BigleafConstants`](@ref)`()`: エントリを持つ辞書 

      * `Pr` - プランドル数

# 詳細

他の量 x の境界層伝導率は、熱伝達の境界層に基づいて次のように計算されます (Hicks et al. 1987):

$$
Gb_x = Gb_h / (Sc_x / Pr)^{0.67}
$$

ここで `Sc_x` は量 x のシュミット数であり、Pr はプランドル数 (0.71) です。

# 値

`Gb_x` というキーを持つ NameTuple または `df` で、ここで `x` は `Sc` のキーであり、対応する境界層伝導率 (m s-1) です。

# 例

```jldoctest; output=false
using DataFrames
df = DataFrame(Gb_h=[0.02, missing, 0.055])
add_Gb!(df, :O2 => 0.84, :CH4 => 0.99)
propertynames(df)[2:3] == [:Gb_O2, :Gb_CH4]
# output
true
```

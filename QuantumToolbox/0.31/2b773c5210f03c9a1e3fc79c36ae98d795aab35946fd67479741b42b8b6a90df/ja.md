```
convert_unit(value::Real, unit1::Symbol, unit2::Symbol)
```

エネルギー `value` を `unit1` から `unit2` に変換します。 `unit1` と `unit2` は以下の `Symbol` のいずれかであることができます：

  * `:J` : ジュール
  * `:eV` : 電子ボルト
  * `:meV` : ミリ電子ボルト
  * `:MHz` : プランク定数 $h$ で乗算されたメガヘルツ
  * `:GHz` : プランク定数 $h$ で乗算されたギガヘルツ
  * `:K` : ボルツマン定数 $k$ で乗算されたケルビン
  * `:mK` : ボルツマン定数 $k$ で乗算されたミリケルビン

変換には [`PhysicalConstants`](@ref) に格納されている値を使用します。

# 例

```jldoctest
julia> convert_unit(1, :eV, :J)
1.602176634e-19

julia> convert_unit(1, :GHz, :J)
6.62607015e-25

julia> round(convert_unit(1, :meV, :mK), digits=4)
11604.5181
```

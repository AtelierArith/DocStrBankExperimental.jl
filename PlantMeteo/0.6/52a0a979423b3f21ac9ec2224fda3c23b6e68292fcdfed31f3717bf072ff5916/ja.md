```
to_daily(df, args...)
to_daily(t::T, args...) where {T<:TimeStepTable{<:Atmosphere}}
```

`DataFrame`オブジェクトまたはサブデイリー時間ステップ（*例* 1h）を持つ`TimeStepTable{<:Atmosphere}`をデイリー時間ステップテーブルに変換します。

# 引数

  * `t`: サブデイリー時間ステップ（*例* 1h）を持つ`TimeStepTable{<:Atmosphere}`
  * `args`: データに適用する変換のリストで、`DataFrames.jl`の形式に従います

# 注意事項

デフォルトの変換がデータに適用され、ユーザーによって上書きすることができます。デフォルトの変換は以下の通りです：

  * `:date => (x -> unique(Dates.Date.(x))) => :date`: 日付が`Date`オブジェクトに変換されます
  * `:duration => sum => :duration`: 期間が合計されます
  * `:T => minimum => :Tmin`: Tminには最小温度が使用されます
  * `:T => maximum => :Tmax`: Tmaxには最大温度が使用されます
  * `:Precipitations => sum => :Precipitations`: 降水量が合計されます
  * `:Rh => mean => :Rh`: 相対湿度が平均されます
  * `:Wind, :P, :Rh, :Cₐ, :e, :eₛ, :VPD, :ρ, :λ, :γ, :ε, :Δ, :clearness`は

すべて平均されます

  * `[:Ri_SW_f, :duration] => ((x, y) -> sum(x .* Dates.toms.(y)) * 1.0e-9) => :Ri_SW_f`: 放射照度が積分されるため、その単位はW m⁻²からMJ m⁻² d⁻¹に変わります
  * その他の放射照度変数も積分されます（詳細はコードを参照）

デフォルトの変換はユーザーによって上書きすることができ、デフォルトの変換は変数が利用可能な場合にのみ適用されることに注意してください。

# 例

```julia
using PlantMeteo, Dates
# 今日と明日の予報：
period = [today(), today()+Dates.Day(1)]
w = get_weather(48.8566, 2.3522, period)
# デイリーに変換：
w_daily = to_daily(w, :T => mean => :Tmean)
```

```
get_soil_(symbols, simulation; depths_to_read_out_mm = nothing, days_to_read_out_d = nothing))
```

土壌層を列、時間ステップを行とする土壌変数の2D DataFrameを返します。サポートされる変数は次のとおりです：     - `:θ` (= `:theta`) = 体積土壌水分値 (m3/m3)     - `:ψ` (= `:psi`) = 土壌マトリックポテンシャル (kPa)     - `:W` = 土壌湿度 (-)     - `:SWATI` = 離散化された層に含まれる土壌水量 (mm)     - `:K` = 土壌水理伝導率 (mm/day)     - `:δ18O`, `:δ2H`, `:d18O`, `:d2H` = 同位体サイン (デルタ)     - `TRANI`, `RWU` = 各セルからの根の水分吸収フラックス (mm/day) ユーザーは、`days_to_read_out_d`として時間ステップを、または`depths_to_read_out_mm`として特定の深さを定義できます。これらはどちらも数値ベクトルとしてオプションで提供されます。例：`depths_to_read_out_mm = [100, 150]` または `days_to_read_out_d = 1:1.0:100`

シミュレーションから土壌変数を読み出すための関数です。

  * `symbols`: 単一のシンボル (:θ) またはシンボルのベクトル [:θ] または [:θ, :ψ, :δ18O, :δ2H, :W, :SWATI, :K] であることができます。

      * 非Unicodeシンボルも受け付けられます：例 [:theta, :psi, :delta18O, :delta2H, :d18O, :d2H]
  * `simulation`: シミュレーションされた `DiscretizedSPAC` です。
  * `depths_to_read_out_mm`: `nothing` または整数のベクトルです。
  * `days_to_read_out_d`: `nothing` または日数を表す浮動小数点数のベクトルです。

例     get*soil*(:θ, simulation)     get*soil*([:θ, :ψ, :K], simulation; depths*to*read*out*mm = [100, 200, 500, 1200])

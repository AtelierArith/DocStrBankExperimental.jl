```
chamber(composition::Union{Silicic,Mafic}, end_time::Float64, log_volume_km3::Float64, InitialConc_H2O::Float64, InitialConc_CO2::Float64, log_vfr::Float64, depth::Float64, output_dirname::String; kwargs...)
```

火山の噴火を、DegruyterとHuber（2014）に基づく上部地殻マグマチャンバーの噴火頻度モデルを使用してシミュレートします。

## 引数

  * `composition`: マグマの組成。リオライト組成（弧マグマ）の場合は`Silicic()`を、玄武岩組成（リフト）の場合は`Mafic()`を使用します。
  * `end_time`: マグマチャンバーの進化の最大持続時間（秒）。
  * `log_volume_km3`: チャンバーの初期体積の対数スケール。実際の初期チャンバー体積は10^(`log_volume_km3`)として計算され、単位はkm³です。
  * `InitialConc_H2O`: マグマ中の水の初期重量分率（析出 + 溶解）。
  * `InitialConc_CO2`: マグマ中のCO₂の初期重量分率（析出 + 溶解）。
  * `log_vfr`: マグマの再充填率（km³/年）で、10^(`log_vfr`)として計算されます。
  * `depth`: マグマチャンバーの深さ（メートル）。
  * `output_dirname`（オプション）: 出力ディレクトリの名前。デフォルトは現在のタイムスタンプです。

## キーワード引数

  * `plotfig`（オプション）: （デフォルト: `true`）。結果ごとに図を生成してプロットする場合はtrueにします。

## 戻り値

以下の列を含む`DataFrame`が返されます。

  * `time`: シミュレーションのタイムスタンプ（秒）。
  * `P+dP`: 圧力（Pa）。
  * `T`: 温度（K）。
  * `eps_g`: ガス体積分率。
  * `V`: マグマチャンバーの体積（m³）。
  * `rho_m`: 溶融物の密度（kg/m³）。
  * `rho_x`: マグマ結晶の密度（kg/m³）。
  * `X_CO2`: ガス中のCO2のモル分率。
  * `total_mass`: マグマチャンバーの総質量（kg）。
  * `total_mass_H2O`: マグマ中の水の総質量（kg）。
  * `total_mass_CO2`: マグマ中のCO₂の総質量（kg）。
  * `eps_x`: 結晶体積分率。

## 出力

`output_dirname`またはデフォルト値にちなんだ名前のディレクトリが作成され、以下のファイルが含まれます。

  * `out.csv`: 上記の解決列を含むCSVファイル。
  * `eruptions.csv`: 噴火のデータを含むCSVファイルで、以下の列が含まれます: 噴火の時間（秒）、噴火の持続時間（秒）、噴出した質量（kg）、噴出した体積（km³）。
  * P+dP(t)、T(t)、eps*g(t)、V(t)、X*CO2(t)、total_mass(t)の図。

## 参考文献

  * W. Degruyter and C. Huber (2014). 上部地殻のシリシックマグマチャンバーの噴火頻度モデル。地球惑星科学レター。 https://doi.org/10.1016/j.epsl.2014.06.047

## 例

```
# シリシックマグマチャンバーでシミュレーションを実行
julia> composition = Silicic()
julia> end_time = 3e9
julia> log_volume_km3 = 0.2
julia> InitialConc_H2O = 0.04
julia> InitialConc_CO2 = 0.001
julia> log_vfr = -3.3
julia> depth = 8e3

julia> chamber(composition, end_time, log_volume_km3, InitialConc_H2O, InitialConc_CO2, log_vfr, depth)

# マフィックマグマチャンバーでシミュレーションを実行し、カスタムディレクトリ名"MyDirname"を指定
julia> composition = Mafic()
julia> end_time = 3e9
julia> log_volume_km3 = 0.2
julia> InitialConc_H2O = 0.01
julia> InitialConc_CO2 = 0.001
julia> log_vfr = -3.3
julia> depth = 8e3
julia> output_dirname = "MyDirname"

julia> chamber(composition, end_time, log_volume_km3, InitialConc_H2O, InitialConc_CO2, log_vfr, depth, output_dirname)
```

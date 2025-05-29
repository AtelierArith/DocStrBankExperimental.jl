```
write_measurements!(model::Type, data::Dict, pf_results::Dict, path::String; exclude::Vector{String}=String[], σ::Float64=0.005)
```

測定値を含むcsvファイルを書き込むための関数で、状態推定計算を実行するために使用されます。このファイルは、PowerModelsDistribution.jl（または同じ形式の辞書）からの電力フロー結果を基に構築されます。測定値は、すべての発電機と負荷に対応する電圧および電力/電流注入で構成されます。正確な測定タイプは、選択した電力フローの定式化に依存します。たとえば、AC極形式の場合、これらは電圧の大きさと有効および無効電力です。

# 引数

  * `model`: 生成された測定値の電力フロータイプ、例：ACPUPowerModel。            `pf_results`の電力フローモデルと一致しない場合、機能しない可能性があります。            `pf_results`は後処理可能で、たとえば、極形式の結果を直交形式に変換            したり、その逆を行ったりして、結果の辞書を互換性のあるものにすることができます。
  * `data`: PowerModelsDistributionで使用可能な形式の数学的データ辞書
  * `pf_results`: PowerModelsDistributionの解辞書または同様の形式
  * `path`: csvファイルが生成され保存されるパス
  * `exclude`: 測定生成から除外するために`pf_results`辞書から選択する量。              たとえば、ACPUPowerModelで発電機の結果を無視するには、              exclude = ["pg", "qg"]に設定します。
  * `σ`: 需要/発電測定の標準偏差。浮動小数点数の場合、相対バス電圧測定の標準偏差が`get_sigma()`で取得されます。辞書（推奨オプション）の場合、各測定量の個別のσが宣言されます。

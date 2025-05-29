```
fit_KPFM!(grid::SpmGrid, response_channel::String;
    sweep_channel::String="", bwd::Bool=true)::Nothing
```

KPFMデータをフィッティングします。これは、グリッド上の`sweep_channel`に対する`response_channel`のグラフに放物線をフィッティングすることによって行われます。明示的に指定されていない場合、`sweep_channel`はグリッドのスイープ信号にデフォルト設定されます。

KPFMの場合、レスポンスチャネルは「周波数シフト」チャネルであり、スイープチャネルは「バイアス」です。

パラメータ「KPFM:Bias」、「KPFM:Frequency Shift」、「KPFM:Residuals AbsSum」とチャネル「KPFM:Fit」、「KPFM:Residuals」をSpmGrid `grid`に追加します。

`bwd`が`true`（デフォルト）である場合、プロットにはバックワードスイープからのデータも含まれます（存在する場合）。

```
deconvolve_force!(grid::SpmGrid, response_channel::String,
    f₀::Float64=0., A::Float64=0., k::Float64=1800.;
    sweep_channel::String="", bwd::Bool=true)::Nothing
```

[Sadar Jarvis力のデコンボリューションアルゴリズム](https://aip.scitation.org/doi/10.1063/1.1667267)を、[SpmSpectroscopy](https://github.com/alexriss/SpmSpectroscopy.jl)パッケージに実装された通りに、`grid`内の各点に適用します。`response_channel`は「周波数シフト」チャネルを指し、`sweep_channel`（デフォルトはグリッドのスイープ信号）はチップ高さ「Z」を指す必要があります。

さらに、実験パラメータとして`f₀`（共鳴周波数）、`A`（振動振幅）、および`k`（カンチレバー剛性）を指定できます。`k`のデフォルト値は1800 N/mで、これは[ qPlusセンサー](https://doi.org/10.1063/1.5052264)の典型的な値です。`f₀`と`A`の値がデフォルト値の`0.`のままにされている場合、値はヘッダーデータから抽出されます。

`SpmGrid` `grid`にチャネル「Force z」と「Potential」を追加します。さらに、チャネル「Force x」と「Force y」は、それぞれx方向とy方向のPotentialの微分によって計算されます。`sweep_channel`がソートされていない場合、xおよびyの力成分は計算されません。

`bwd`が`true`（デフォルト）の場合、プロットには後方スイープからのデータも含まれます（存在する場合）。

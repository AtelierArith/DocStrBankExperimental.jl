```
runcircuit(
  M::Union{MPS, MPO, ITensor},
  circuit::Vector{<:Vector{<:ITensor}};
  (observer!)=nothing,
  move_sites_back_before_measurements::Bool=false,
  noise = nothing,
  outputlevel = 1,
  outputpath = nothing,
  savestate = false,
  print_metrics = [],
  kwargs...)
```

入力状態 `M` に量子回路を適用します。ここで、回路は量子ゲートの層のシーケンスで構成されています。入力状態は、MPS 波動関数 $|\psi\rangle$、MPO 密度演算子 $ρ$（またはユニタリ演算子 $U$）などである可能性があります。

「層状」の回路を供給することで、測定を有効にし、回路の深さの関数としてメトリクスを追跡できます。

高レベルインターフェースのキーワード引数の他に、ここで提供できるものは次のとおりです：

  * `(observer!)`: 観測者オブジェクト（Observers.jlから）。
  * `outputlevel = 1`: 計算中の印刷量。
  * `outputpath = nothing`: 設定されている場合、ファイルに観測者を保存します。
  * `savestate = false`: `true` の場合、`MPS/MPO` をファイルに保存します。
  * `print_metrics = []`: 各深さで印刷する `observed` のメトリクス。`

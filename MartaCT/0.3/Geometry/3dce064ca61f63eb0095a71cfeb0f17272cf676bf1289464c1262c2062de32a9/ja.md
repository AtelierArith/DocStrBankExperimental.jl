```
ParallelBeamGeometry([T=Float32]; <キーワード引数>) where {T}
```

シミュレーションのためのジオメトリを構築します。

# 引数

  * `nϕ`: プロジェクションの数。
  * `nd=nothing`: 検出器の数。指定されていない場合、`nϕ`と同じ。
  * `rows=nothing`: 再構成された画像の行数。指定されていない場合、`nd`と同じ。
  * `cols=nothing`: 再構成された画像の列数。指定されていない場合、`rows`と同じ。
  * `width=nothing`: `cols`のエイリアス。
  * `height=nothing`: `rows`のエイリアス。
  * `α=360`: スキャン角度（度）。
  * `α₀=0`: スキャン開始角度（度）。
  * `center=nothing`: 仮想中心チャネル、デフォルトは`(nd-1)/2`。

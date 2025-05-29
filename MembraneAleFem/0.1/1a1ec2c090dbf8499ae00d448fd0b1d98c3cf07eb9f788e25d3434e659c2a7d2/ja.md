```
シナリオ
```

シミュレーションするシナリオ: `instances(Scenario)`

  * `F_CAVI = 1` –> 蓋駆動キャビティ
  * `F_COUE = 2` –> クーエット流
  * `F_POIS = 3` –> ハーゲン–ポワズイユ流
  * `F_PULL = 4` –> 平面パッチからの引っ張り
  * `F_BEND = 5` –> 平面パッチの曲げ

最初の文字はメッシュ [`Topology`](@ref) を示します: `F` は平面パッチ、`C` はシリンダーです。現在、シリンダーシナリオは実装されていません。

新しいシナリオを作成するには:

  * `Scenario` 列挙型に新しいエントリを追加してエクスポートする
  * `src/input/Bc.jl` の [`get_scenario_bc_info`](@ref) を編集する
  * `src/input/Mesh.jl` に対応する `apply_<SCENARIO>_bcs` 関数を書く
  * `src/input/Params.jl` の `implemented` リストに新しい `scenario` を追加する

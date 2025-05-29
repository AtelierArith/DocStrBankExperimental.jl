```
DisplaySimulator(;kwargs...)
```

シミュレーションの各ステップを表示するシミュレーターを作成します。

POMDPまたはMDPモデル`m`が与えられた場合、このシミュレーターは大まかに次のように動作します。

```
for step in stepthrough(m, ...)
    display(render(m, step))
end
```

# キーワード引数

  * `display::AbstractDisplay`: `display`関数への最初の引数として使用する表示。これが`nothing`の場合、`display(...)`は`AbstractDisplay`引数なしで呼び出されます。
  * `render_kwargs::NamedTuple`: `POMDPTools.render(...)`のためのキーワード引数
  * `max_fps::Number=10`: 1秒あたりに表示される最大フレーム数 - `sleep`が余分な時間をスキップするために使用されるので、高精度のためには設計されていません
  * `predisplay::Function`: `display(...)`の呼び出しの前に呼び出す関数。この関数への唯一の引数は表示（指定されている場合）または`nothing`です
  * `extra_initial::Bool=false`: `true`の場合、POMDPの要素`t`、`sp`、および`bp`のみを持つ追加のステップを最初に表示します（`render`が`s`ではなく`sp`のみを表示する場合、初期状態を見るのに便利です）。
  * `extra_final`::Bool=true`:`true`の場合、POMDPの要素`t`、`done`、`s`、および`b`のみを持つ追加のステップを最後に表示します（`render`が`sp`ではなく`s`のみを表示する場合、最終状態を見るのに便利です）。
  * `max_steps::Integer`: 実行する最大ステップ数
  * `spec::NTuple{Symbol}`: 表示するステップ要素の仕様（`eachstep`を参照）
  * `rng::AbstractRNG`: 擬似乱数生成器

特定の表示を使用するためのヒントについては、POMDPSimulatorsのドキュメントを参照してください。

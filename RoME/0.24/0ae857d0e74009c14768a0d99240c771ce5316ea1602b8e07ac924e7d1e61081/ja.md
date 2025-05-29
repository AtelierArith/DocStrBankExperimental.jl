```julia
manageSolveTree!(dfg, mss; dbg, timinglog, limitfixeddown)

```

非同期ソルバーマネージャーで、他のタスクが共通の分散ファクターグラフオブジェクトを変更している間に同時に実行できます。

ノート

  * 変数とファクターを追加する際は、推論の準備ができるまで新しいフラグメントを無効にするために `solvable=0` を使用してください。

      * 例: `addVariable!(fg, :x45, Pose2, solvable=0)`
      * ファクターグラフのこれらの部分は、解決のために単にアクティブにすることができます `setSolvable!(fg, :x45, 1)`

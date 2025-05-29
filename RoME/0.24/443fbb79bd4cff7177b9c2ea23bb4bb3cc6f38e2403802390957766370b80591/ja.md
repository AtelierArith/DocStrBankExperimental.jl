```julia
setSolvableOldPoses!(
    dfg;
    youngest,
    oldest,
    solvable,
    filterLabel
)

```

古いポーズと隣接する因子を `solvable::Int=0`（デフォルト）に設定します。

ノート

  * `youngest::Int` と `oldest::Int` はカウントによる検索の限界を設定します。

      * `oldest` は、ソルバーループが再発サイクルで古い部分を確実に切り離すのに十分大きく設定します。
  * `filterLabel::Regex` は、各ポーズラベルを検索するためのテンプレートを設定します。
  * ポーズは、ローカル探索変数を接続する時間を通じたスレッドであると仮定されます。
  * 最初は、固定遅延周辺化と組み合わせて、ソリューションから古い変数と因子を削除するために開発されました。

      * `getSolverParams(fg).isfixedlag=true`

関連:

getLastPoses

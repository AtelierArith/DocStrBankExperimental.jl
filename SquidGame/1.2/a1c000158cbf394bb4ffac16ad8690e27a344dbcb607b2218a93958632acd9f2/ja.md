```
Game(; rewards, num_rounds, num_players=length(size(rewards(1))), show_rounds_left=true)
```

タイプ `Game` のゲームを構築します。警告: 開発者は、以下の仮定が成り立たない場合、インフラが機能するかどうか確信が持てません:

  * インデックスは対称的です（プレイヤー `s` のアクション `i` は、プレイヤー `k` のアクション `i` と同じです ∀i,s,k）。

引数:

  * `rewards::Function`: 各ラウンドの報酬を返す関数（`rewards(round) -> Array{Float64, num_players}`）;
  * `num_rounds::Int`: ゲームのラウンド数;
  * `num_players::Int`: ゲームのプレイヤー数;
  * `show_rounds_left::Bool`: 設定されている場合、ゲームは各ラウンドで残りのラウンド数を開示します。

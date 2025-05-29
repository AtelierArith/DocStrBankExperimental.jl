```
EndgameOptions(; options...)
```

[`EndgameTracker`](@ref) の動作を制御するオプション。

## オプション

  * `at_infinity_check = true`: 発散する経路を切り詰めるべきかどうか。
  * `endgame_start = 0.1`: エンドゲームが始まる時間 `t` のポイント。エンドゲームを無効にするには `0.0` に設定します。
  * `only_nonsingular = false`: `true` の場合、特異解を処理するためにコーシーエンドゲームを実行しません。
  * `zero_is_at_infinity = false`: 1つ以上の座標がゼロの解に向かう経路も発散と見なすべきかどうか。

### パラメータ

これらのパラメータはエンドゲーム中の動作を制御します。

  * `max_endgame_steps = 2000`: エンドゲーム中に実行される最大ステップ数。
  * `max_winding_number = 6`: コーシーエンドゲームで試みられる最大巻き数。
  * `min_cond = 1e6`: エンドゲーム戦略が適用されると見なされる最小条件数。
  * `min_cond_growth = 1e4`: エンドゲーム戦略が適用されると見なされる最小条件数の成長。
  * `min_coord_growth = 100`: 無限大（またはゼロ）に向かうと見なされるために必要な座標の最小相対成長。
  * `singular_min_accuracy = 1e-6`: 解はその [`accuracy`](@ref) がこの閾値を下回る場合にのみ特異エンドゲーム法で扱うことができます。そうでない場合、解は洗練されるか、未成功の終了としてラベル付けされます。
  * `val_at_infinity_tol = 1e-3`: 経路が発散する/無限大に向かうと見なされる前に満たす必要がある評価の許容範囲。
  * `val_finite_tol = 1e-3`: エンドゲームが開始される前に満たす必要がある評価の許容範囲。
  * `sing_cond = 1e14`: 解が特異と見なされる条件数の値。
  * `sing_accuracy = 1e-12`: 解が特異と見なされる [`accuracy`](@ref) の値。
  * `scaling_threshold = -30.0`: 行のスケーリングは、行のノルムが `2^e` であると推定される `e < scaling_threshold` の行にのみ適用されます。詳細については [`skeel_row_scaling`](@skeel_row_scaling) を参照してください。
  * `refine_steps = 3`: 最後に解を洗練するためのステップ数。

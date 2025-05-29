```
get_1d_interpolator(xs, ys; <キーワード引数>)
```

テーブル `xs, ys` に対して 1D 補間器 `F(x) ≈ y` を取得します。デフォルトでは定数外挿を行います。

# 引数

  * `xs`: パラメータポイントのソートされたリスト。
  * `ys`: `xs` と同じ長さの関数値のリスト。
  * `method=LinearInterpolant`: 補間のためのコンストラクタ。デフォルトは単純な線形補間を行う `LinearInterpolant` です。
  * `cap_endpoints = true`: エンドポイントがキャップされるように値を追加します（定数外挿）。そうでない場合、外挿はメソッドに一致します。
  * `cap_start = cap_endpoints`: 区間の開始部分のみの `cap_endpoints` の細かいバージョン（`x < xs[1]` の外挿）。
  * `cap_end = cap_endpoints`: 区間の終了部分のみの `cap_endpoints` の細かいバージョン（`x > xs[end]` の外挿）。

追加のキーワード引数は補間器のコンストラクタに渡されます。

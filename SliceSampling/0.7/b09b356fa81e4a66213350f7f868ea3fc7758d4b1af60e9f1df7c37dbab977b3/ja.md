```
SliceDoublingOut(window; max_doubling_out, max_proposals)
```

一変量スライスサンプリングは、「ダブリングアウト」手法によって初期区間を自動的に適応させます（Nealによるスキーム4[^N2003]）

# 引数

  * `window::Real`: 提案ウィンドウ。

# キーワード引数

  * `max_doubling_out`: 最大「ダブリングアウト」の数（デフォルト: 8）。
  * `max_proposals::Int`: エラーを投げるまでに許可される最大提案数（デフォルト: `10000`）。

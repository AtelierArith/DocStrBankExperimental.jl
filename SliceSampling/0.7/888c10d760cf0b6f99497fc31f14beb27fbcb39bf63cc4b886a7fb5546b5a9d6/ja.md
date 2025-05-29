```
SliceSteppingOut(window; max_stepping_out, max_proposals)
```

一変量スライスサンプリングは、「ステッピングアウト」手法を通じて初期区間を自動的に適応させます（Nealによるスキーム3[^N2003]）

# 引数

  * `window::Real`: 提案ウィンドウ。

# キーワード引数

  * `max_stepping_out::Int`: 最大「ステッピングアウト」の数（デフォルト: 32）。
  * `max_proposals::Int`: エラーを投げるまでに許可される最大提案数（デフォルト: `10000`）。

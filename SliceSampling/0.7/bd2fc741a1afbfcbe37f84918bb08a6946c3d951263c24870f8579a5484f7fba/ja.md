```
Slice(window; max_proposals)
```

固定初期区間を用いた単変量スライスサンプリング（Nealによるスキーム2[^N2003]）

# 引数

  * `window::Real`: 提案ウィンドウ。

# キーワード引数

  * `max_proposals::Int`: エラーを投げるまでに許可される最大提案数（デフォルト: `10000`）。

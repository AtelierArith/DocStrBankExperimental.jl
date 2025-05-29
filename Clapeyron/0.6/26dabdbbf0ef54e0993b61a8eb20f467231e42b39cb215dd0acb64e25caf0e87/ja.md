```
result = ph_flash(model, p, h, n, method::FlashMethod = GeneralizedXYFlash())
result = ph_flash(model, p, h, n; kwargs...)
```

非反応性二相多成分フラッシュ問題をP-H仕様で解決するためのルーチン。[Clapeyron.xy_flash](@ref)のラッパーで、初期点の自動計算を行います。 入力:

  * `p`、圧力
  * `h`、エンタルピー
  * `z`、各種のモル数のベクトル

すべてのキーワード引数は[`GeneralizedXYFlash`](@ref)に転送されます。

出力:

  * `result`、モル分率、蒸気分率、モル体積、平衡温度および圧力を含む[`FlashResult`](@ref)構造体。

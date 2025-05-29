```
result = ps_flash(model, p, s, n, method::FlashMethod = GeneralizedXYFlash())
result = ps_flash(model, p, s, n; kwargs...)
```

反応しない二相多成分フラッシュ問題を解決するルーチン。P-S仕様に基づいています。[Clapeyron.xy_flash](@ref)のラッパーで、自動初期点計算を行います。 入力:

  * `p`、圧力
  * `s`、エントロピー
  * `z`、各種のモル数のベクトル

すべてのキーワード引数は[`GeneralizedXYFlash`](@ref)に転送されます。

出力:

  * `result`、モル分率、蒸気分率、モル体積、平衡温度および圧力を含む[`FlashResult`](@ref)構造体。

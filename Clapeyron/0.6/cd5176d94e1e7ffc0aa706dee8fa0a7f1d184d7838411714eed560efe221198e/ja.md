```
result = vt_flash(model, v, T, n, method::FlashMethod = GeneralizedXYFlash())
result = vt_flash(model, v, T, n; kwargs...)
```

反応しない二相多成分フラッシュ問題を解決するルーチン。V-T仕様を持つ。[Clapeyron.xy_flash](@ref)のラッパーで、自動初期点計算を行います。 入力:

  * `v`, 体積
  * `T`, 温度
  * `z`, 各種のモル数のベクトル

すべてのキーワード引数は[`GeneralizedXYFlash`](@ref)に転送されます。

出力:

  * `result`, モル分率、蒸気分率、モル体積、平衡温度および圧力を含む[`FlashResult`](@ref)構造体。

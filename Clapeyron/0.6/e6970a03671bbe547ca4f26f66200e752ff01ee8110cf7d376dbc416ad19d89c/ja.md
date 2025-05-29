```
result = qt_flash(model, q, T, n, method::FlashMethod = GeneralizedXYFlash())
result = qt_flash(model, q, T, n; kwargs...)
```

非反応性二相多成分フラッシュ問題を解決するためのルーチン。蒸気分率 - T仕様。自動初期点計算を伴う[Clapeyron.xy_flash](@ref)のラッパー。入力:

  * `q`、蒸気分率
  * `T`、温度
  * `z`、各種のモル数のベクトル

すべてのキーワード引数は[`GeneralizedXYFlash`](@ref)に転送されます。

出力:

  * `result`、モル分率、蒸気分率、モル体積、平衡温度および圧力を含む[`FlashResult`](@ref)構造体。

!!! note
    `q = 0`または`q = 1`で`qt_flash`を使用することは、バブルまたは露点圧を計算することと同等です。[`bubble_pressure`](@ref)または[`dew_pressure`](@ref)に`GeneralizedXYFlash`をメソッドとして渡すと、`qt_flash`を使用してバブル/露点を計算します。


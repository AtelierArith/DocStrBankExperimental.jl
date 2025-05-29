```
result = qp_flash(model, q, p, n, method::FlashMethod = GeneralizedXYFlash())
result = qp_flash(model, q, p, n; kwargs...)
```

非反応性二相多成分フラッシュ問題を解決するためのルーチン。蒸気分率 - P仕様。自動初期点計算を伴う[Clapeyron.xy_flash](@ref)のラッパー。入力:

  * `q`、蒸気分率
  * `p`、圧力
  * `z`、各成分のモル数のベクトル

すべてのキーワード引数は[`GeneralizedXYFlash`](@ref)に転送されます。

出力:

  * `result`、モル分率、蒸気分率、モル体積、平衡温度および圧力を含む[`FlashResult`](@ref)構造体。

!!! note
    `q = 0`または`q = 1`で`qp_flash`を使用することは、バブルまたは露点温度を計算することと同等です。[`bubble_temperature`](@ref)または[`dew_temperature`](@ref)に`GeneralizedXYFlash`をメソッドとして渡すと、`qp_flash`を使用してバブル/露点を計算します。


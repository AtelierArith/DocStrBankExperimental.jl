```
TFTD(phases::Bool = true, fϵ = 0.05)
```

`TFTDRandomFourier`（略して`TFTD`）サロゲートは、Lucio et al. (2012)[^Lucio2012] によって、切断フーリエサロゲート[^Nakamura2006]（[`TFTS`](@ref)）とデトレンド・リトレンドサロゲートの組み合わせとして提案されました。

`TFTD`という名前の部分は、サロゲート生成の前後に時間系列を切断フーリエ変換（TFT）でデトレンド・リトレンド（D）するという事実に由来しています。したがって、（強く）非定常な時間系列からもサロゲートを生成するために使用できます。

## 実装の詳細

ここでは、ランダムフーリエ信号を生成する前後に信号から最適フィットの線形トレンドが除去/追加されます。原則として、任意のトレンドを除去できますが、これまでのところ、線形オプションのみを提供しています。

関連情報: [`TFTDAAFT`](@ref), [`TFTDIAAFT`](@ref).

[^Nakamura2006]: Nakamura, Tomomichi, Michael Small, and Yoshito Hirata. "Testing for nonlinearity in irregular fluctuations with long-term trends." Physical Review E 74.2 (2006): 026205.

[^Lucio2012]: Lucio, J. H., Valdés, R., & Rodríguez, L. R. (2012). Improvements to surrogate data methods for nonstationary time series. Physical Review E, 85(5), 056202.

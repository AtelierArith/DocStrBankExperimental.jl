```
SiteParameters
```

カスタムタイプで、フーリエスペクトルのサイトパラメータを定義します。

  * `κ0::T where T<:Real` は、単位が秒のサイトカッパです。
  * `ζ0::U where U<:Real` は、Haendel et al. (2020) の ζ パラメータ（基準周波数 $f_0=1$ Hz の場合）
  * `η::V where V<:Real` は、Haendel et al. (2020) の η パラメータです。
  * `model::W where W<:SiteAmplification` は、インピーダンス関数を定義するサイト増幅モデルです。

引数 `model` は現在次のいずれかです：

  * `SiteAmpUnit` は一般的な単位増幅のためのものです。
  * `SiteAmpBoore2016` は、$V_{S,30}=760$ m/s のための Boore (2016) 増幅です。
  * `SiteAmpAlAtikAbrahamson2021_ask14_620` は、$V_{S,30}=620$ m/s のための Al Atik & Abrahamson (2021) の ASK14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_ask14_760` は、$V_{S,30}=760$ m/s のための Al Atik & Abrahamson (2021) の ASK14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_ask14_1100` は、$V_{S,30}=1100$ m/s のための Al Atik & Abrahamson (2021) の ASK14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_bssa14_620` は、$V_{S,30}=620$ m/s のための Al Atik & Abrahamson (2021) の BSSA14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_bssa14_760` は、$V_{S,30}=760$ m/s のための Al Atik & Abrahamson (2021) の BSSA14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_bssa14_1100` は、$V_{S,30}=1100$ m/s のための Al Atik & Abrahamson (2021) の BSSA14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_cb14_620` は、$V_{S,30}=620$ m/s のための Al Atik & Abrahamson (2021) の CB14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_cb14_760` は、$V_{S,30}=760$ m/s のための Al Atik & Abrahamson (2021) の CB14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_cb14_1100` は、$V_{S,30}=1100$ m/s のための Al Atik & Abrahamson (2021) の CB14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_cy14_620` は、$V_{S,30}=620$ m/s のための Al Atik & Abrahamson (2021) の CY14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_cy14_760` は、$V_{S,30}=760$ m/s のための Al Atik & Abrahamson (2021) の CY14 の逆変換です。
  * `SiteAmpAlAtikAbrahamson2021_cy14_1100` は、$V_{S,30}=1100$ m/s のための Al Atik & Abrahamson (2021) の CY14 の逆変換です。

参照： [`FourierParameters`](@ref), [`site_amplification`](@ref)

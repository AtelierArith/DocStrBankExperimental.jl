```
   simulate(comp::Material, dose::Float64, e0::Float64, θtoa::Float64, Ω::Float64, det::Detector, resp::Matrix{Float64}; noise=false, vargs...)

指定された組成材料のシミュレーションされたX線スペクトルを計算します。

引数:

  * comp: 材料
  * dose: nA⋅s単位の電子線量
  * e0:   eV単位のビームエネルギー
  * θtoa: ラジアン単位のテイクオフ角
  * Ω:    ステラジアン単位の検出器の固体角
  * det:  検出器モデル
  * resp: 検出器応答

`Spectrum`構造体を返します。
```

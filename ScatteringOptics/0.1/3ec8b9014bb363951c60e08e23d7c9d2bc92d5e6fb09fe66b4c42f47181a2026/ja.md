```julia
abstract type AbstractScatteringModel
```

薄いスクリーン近似に基づく抽象的な異方性散乱モデルです。このパッケージでは、Psaltis et al. 2018で紹介された双極子（`DipoleScatteringModel`）、フォン・ミーゼス（`vonMisesScatteringModel`）、および周期的ボックスカー（`PeriodicBoxCarScatteringModel`）モデルの参照実装を提供します。

**必須フィールド** 散乱モデルは、以下のパラメータによって根本的に支配されます。理想的には、この抽象モデルのサブタイプは、これらの引数のみを持つコンストラクタを持つべきです。

  * `α::Number`: 位相変動のべき乗則指数（コルモゴロフは5/3）。
  * `rin::Number`: cm単位の散乱スクリーンの内スケール。
  * `θmaj::Number`: 指定された参照波長での主軸の角度広がりのFWHM（ミリ秒）。
  * `θmin::Number`: 指定された参照波長での副軸の角度広がりのFWHM（ミリ秒）。
  * `ϕ::Number`: 散乱の主軸の位置角（度）。
  * `λ0::Number`: 散乱モデルの参照波長（cm）。
  * `D::Number`: 観測者から散乱スクリーンまでの距離（cm）。
  * `R::Number`: ソースから散乱スクリーンまでの距離（cm）。

さらに、以下のパラメータは事前に計算する必要があります。

  * `M::Number`: 拡大率パラメータ、D/Rとして定義されます。
  * `Qbar::Number`: 変動の振幅。`calc_Qbar(α, rin_cm, λ0_cm, M, θmaj_rad, θmin_rad)`によって与えられます。
  * `C::Number`: パワースペクトルのスケーリング因子。`calc_C(α, rin_cm, λ0_cm, Qbar)`によって与えられます。
  * `D1maj::Number`: `calc_D1(α, Amaj, Bmaj)`によって与えられます。
  * `D2maj::Number`: `calc_D2(α, Amaj, Bmaj)`によって与えられます。
  * `D1min::Number`: `calc_D1(α, Amin, Bmin)`によって与えられます。
  * `D2min::Number`: `calc_D2(α, Amin, Bmin)`によって与えられます。

**オプションフィールド** 以下は現在メソッドで使用されていませんが、持っていると便利かもしれません。

  * `A::Number`: 非対称パラメータ θmaj*mas/θmin*mas
  * `ζ0::Number`: 別の非対称パラメータ。`calc_ζ0(A)`によって与えられます。
  * `ϕ0`:: 位置角（CCWのDec軸から測定）をRA軸からCWで測定したより伝統的な角度に変換したもの。
  * `Amaj::Number`: カーネルの非対称スケーリングに関連しています。`calc_Amaj(rin_cm, λ0_cm, M, θmaj_rad)`によって与えられます。
  * `Amin::Number`: カーネルの非対称スケーリングに関連しています。`calc_Amin(rin_cm, λ0_cm, M, θmin_rad)`によって与えられます。
  * `Bmaj::Number`: `calc*Bmaj(α, ϕ0, Pϕfunc, B*prefac)`によって与えられます。
  * `Bmin::Number`: `calc*Bmin(α, ϕ0, Pϕfunc, B*prefac)`によって与えられます。

**必須メソッド**

  * `Pϕ(sm::ScatteringModel, ϕ)`: 磁場の方向の変動の確率分布で、方向はϕ0に中心を持ちます。

```
InterfaceValues
```

`InterfaceValues`オブジェクトは、要素間のインターフェース上での形状関数や関数の値、平均、ジャンプ、勾配を評価するプロセスを容易にします。

インターフェースの最初の要素は「ここ」と呼ばれ、2番目の要素は「そこ」と呼ばれます。

**コンストラクタ**

  * `InterfaceValues(qr::FacetQuadratureRule, ip::Interpolation)`: 両側で同じ数値積分ルールと補間を使用し、デフォルトの線形ラグランジュ幾何補間を使用します。
  * `InterfaceValues(qr::FacetQuadratureRule, ip::Interpolation, ip_geo::Interpolation)`: 上記と同様ですが、指定された幾何補間を使用します。
  * `InterfaceValues(qr_here::FacetQuadratureRule, ip_here::Interpolation, qr_there::FacetQuadratureRule, ip_there::Interpolation)`: 両側で異なる数値積分ルールと補間を使用し、デフォルトの線形ラグランジュ幾何補間を使用します。
  * `InterfaceValues(qr_here::FacetQuadratureRule, ip_here::Interpolation, ip_geo_here::Interpolation, qr_there::FacetQuadratureRule, ip_there::Interpolation, ip_geo_there::Interpolation)`: 上記と同様ですが、指定された幾何補間を使用します。
  * `InterfaceValues(fv::FacetValues)`: フェイス値からの数値積分ルールと補間（両側で同じ）。
  * `InterfaceValues(fv_here::FacetValues, fv_there::FacetValues)`: フェイス値からの数値積分ルールと補間。

**関連メソッド:**

  * [`shape_value_average`](@ref)
  * [`shape_value_jump`](@ref)
  * [`shape_gradient_average`](@ref)
  * [`shape_gradient_jump`](@ref)

**共通メソッド:**

  * [`reinit!`](@ref)
  * [`getnquadpoints`](@ref)
  * [`getdetJdV`](@ref)
  * [`shape_value`](@ref)
  * [`shape_gradient`](@ref)
  * [`shape_divergence`](@ref)
  * [`shape_curl`](@ref)
  * [`function_value`](@ref)
  * [`function_gradient`](@ref)
  * [`function_symmetric_gradient`](@ref)
  * [`function_divergence`](@ref)
  * [`function_curl`](@ref)
  * [`spatial_coordinate`](@ref)

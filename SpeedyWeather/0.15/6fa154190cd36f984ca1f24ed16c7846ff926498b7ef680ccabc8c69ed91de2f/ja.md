```julia
set!(
    progn::SpeedyWeather.PrognosticVariables,
    geometry::SpeedyWeather.Geometry;
    u,
    v,
    vor,
    div,
    temp,
    humid,
    pres,
    sea_surface_temperature,
    sea_ice_concentration,
    soil_temperature,
    snow_depth,
    soil_moisture,
    lf,
    add,
    spectral_transform,
    coslat_scaling_included,
    kwargs...
)

```

キーワード引数（速度、渦度、発散など）の新しい値を、タイムステップインデックス `lf` の予測変数構造体 `progn` に設定します。`add==true` の場合、現在の値に追加されます。`SpectralTransform` S が提供されている場合、変数を設定する必要があるときに使用され、それ以外の場合は再計算されます。`u` と `v` が提供されている場合、実際には発散と渦度が設定され、`coslat_scaling_included` は 1/cos(lat) スケーリングが配列にすでに含まれているかどうかを指定します（デフォルト: `false`）

入力は次のようになります：

  * 関数または呼び出し可能オブジェクト `f(lond, latd, σ) -> value`（多層変数）
  * 関数または呼び出し可能オブジェクト `f(lond, latd) -> value`（表面レベル変数）
  * `AbstractGridArray` のインスタンス
  * `LowerTriangularArray` のインスタンス
  * スカラー `<: Number`（グリッド空間内の定数フィールドとして解釈される）

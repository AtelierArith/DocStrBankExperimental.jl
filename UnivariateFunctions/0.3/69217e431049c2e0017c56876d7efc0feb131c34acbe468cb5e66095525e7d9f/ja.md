```
create_quadratic_spline(x::Union{Vector{DateTime},Vector{Date},Vector{Union{Date,DateTime}}},y::Vector{<:Real} ; gradients::Union{Missing,Vector{<:Real}} = missing, extrapolation::Tuple{Schumaker_ExtrapolationSchemes,Schumaker_ExtrapolationSchemes} = (Curve,Curve),
                             left_gradient::Union{Missing,Real} = missing, right_gradient::Union{Missing,Real} = missing)
create_quadratic_spline(x::Vector{<:Real},y::Vector{<:Real} ; gradients::Union{Missing,Array{<:Real}} = missing, extrapolation::Tuple{Schumaker_ExtrapolationSchemes,Schumaker_ExtrapolationSchemes} = (Curve,Curve),
                             left_gradient::Union{Missing,Real} = missing, right_gradient::Union{Missing,Real} = missing)
create_quadratic_spline(x::Union{Vector{D},Vector{<:DatePeriod}},y::Vector{<:Real}; gradients::Union{Missing,Vector{<:Real}} = missing, extrapolation::Tuple{Schumaker_ExtrapolationSchemes,Schumaker_ExtrapolationSchemes} = (Curve,Curve),
                             left_gradient::Union{Missing,Real} = missing, right_gradient::Union{Missing,Real} = missing) where D<:DatePeriod
```

SchumakerSpline.jlパッケージを使用して、二次の形状を保持する補間スプラインを作成します。これは`Schumaker`構造体ではなく、`Piecewise_Function`として返されます。

### 入力

  * `x` - x座標を持つ`Vector`
  * `y` - y座標を持つ`Vector`
  * `gradients` - 各x位置での勾配を持つ`Vector`。提供されていない場合は計算されます。
  * `extrapolation` - 外挿方法を説明する列挙型のタプル（左側と右側）。
  * `left_gradient` - 左端（つまり最初のx座標）に課す勾配。
  * `right_gradient` - 右端（つまり最後のx座標）に課す勾配。

### 戻り値

  * スプラインを含む`Piecewise_Function`。

```
create_quadratic_spline(schum::Schumaker)
```

これは、`SchumakerSpline.Schumaker`構造体で表されるスプラインを、同じスプラインですが`Piecewise_Function`で表されるものに変換します。

### 入力

  * `schum` - `Schumaker`構造体。

### 戻り値

  * スプラインを含む`Piecewise_Function`。

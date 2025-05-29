```
velocity_ic!(body, set_name, dim, value)
velocity_ic!(fun, body, set_name, dim)
```

`body`内の`set_name`の点の速度初期条件を指定します。初期条件の`value`は時間積分の前に指定されます。関数`fun`が指定されている場合、その関数で値が指定されます。

# 引数

  * `body::AbstractBody`: [`Body`](@ref) が条件が指定される対象です。
  * `set_name::Symbol`: このボディの点セットの名前。
  * `dim::Union{Integer,Symbol}`: 条件の方向で、シンボルまたは整数として指定されます。

      * x方向: `:x` または `1`
      * y方向: `:y` または `2`
      * z方向: `:z` または `3`
  * `value::Real`: 時間積分の前に指定される値。
  * `fun::Function`: 値の計算のための条件関数で、`Float64`を返すべきです。条件関数が`NaN`を返す場合、この値は無視され、指定された位置の条件をオフにするために使用できます。この関数は1つまたは2つの位置引数を受け入れ、引数名を認識します。可能な引数と名前:

      * `fun(p)`: この関数は点の参照位置`p`を`SVector{3}`として受け取ります。

# 例外

  * `set_name`を持つセットがボディに存在しない場合、エラーが発生します。
  * 方向が正しく指定されていない場合、エラーが発生します。
  * 関数が条件関数として適切でなく、引数が間違っている場合、エラーが発生します。

# 例

```julia-repl
julia> velocity_ic!(body, :all_points, :x, -100.0)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  1 initial condition(s):
    IC on velocity: point_set=all_points, dim=1
```

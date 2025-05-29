```
forcedensity_bc!(fun, body, set, dim)
```

ボディ内のセット `set_name` のポイントに対して力密度境界条件を指定します。境界条件の値は、各タイムステップで関数 `fun` によって計算されます。

# 引数

  * `fun::Function`: 値の計算のための条件関数で、`Float64` を返す必要があります。条件関数が `NaN` を返す場合、この値は無視され、指定された時間が経過した後に条件をオフにするために使用できます。この関数は1つまたは2つの位置引数を受け入れ、引数名を認識します。可能な引数と名前:

      * `fun(t)`: 関数は各タイムステップで現在の時間 `t` を受け取ります。これにより、時間とともに変化する条件を指定することが可能になります。
      * `fun(p, t)`: この関数は `set_name` の各ポイントに対して処理され、ポイントの参照位置を `SVector{3}` として受け取り、各タイムステップで現在の時間 `t` を受け取ります。これにより、ポイントの位置にも依存する条件を指定することが可能になります。
  * `body::AbstractBody`: 条件が指定される [`Body`](@ref)。
  * `set_name::Symbol`: このボディのポイントセットの名前。
  * `dim::Union{Integer,Symbol}`: 条件の方向で、シンボルまたは整数として指定されます。

      * x方向: `:x` または `1`
      * y方向: `:y` または `2`
      * z方向: `:z` または `3`

# 例外

  * ボディが `set_name` を持つセットを含まない場合、エラーが発生します。
  * 方向が正しく指定されていない場合、エラーが発生します。
  * 関数が条件関数として適切でなく、引数が間違っている場合、エラーが発生します。

# 例

```julia-repl
julia> forcedensity_bc!(t -> 8000.0, body, :all_points, :x)

julia> forcedensity_bc!((p,t) -> p[1] * t, body, :all_points, :y)

julia> forcedensity_bc!(t -> t > 0.00001 ? 8000.0 : NaN, body, :all_points, :z)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  3 boundary condition(s):
    BC on force density: point_set=all_points, dim=1
    BC on force density: point_set=all_points, dim=3
    Pos.-dep. BC on force density: point_set=all_points, dim=2
```

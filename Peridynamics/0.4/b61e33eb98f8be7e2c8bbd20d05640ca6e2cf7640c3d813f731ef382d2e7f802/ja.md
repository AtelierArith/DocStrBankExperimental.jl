```
velocity_bc!(fun, body, set_name, dim)
```

`body`内の`set_name`の点に対して速度境界条件を指定します。境界条件の値は、毎タイムステップで関数`fun`を用いて計算されます。

# 引数

  * `fun::Function`: 値の計算のための条件関数で、`Float64`を返す必要があります。条件関数が`NaN`を返す場合、その値は無視され、指定された時間が経過した後に条件をオフにするために使用できます。この関数は1つまたは2つの位置引数を受け取り、引数名を認識します。可能な引数と名前:

      * `fun(t)`: この関数は、毎タイムステップで現在の時間`t`を受け取ります。これにより、時間とともに変化する条件を指定することが可能です。
      * `fun(p, t)`: この関数は`set_name`のすべての点に対して処理され、点の参照位置を`SVector{3}`として受け取り、毎タイムステップで現在の時間`t`を受け取ります。これにより、点の位置にも依存する条件を指定することが可能です。
  * `body::AbstractBody`: 条件が指定される[`Body`](@ref)。
  * `set_name::Symbol`: このボディの点セットの名前。
  * `dim::Union{Integer,Symbol}`: 条件の方向で、シンボルまたは整数として指定されます。

      * x方向: `:x`または`1`
      * y方向: `:y`または`2`
      * z方向: `:z`または`3`

# 例外

  * `set_name`を持つセットがボディに含まれていない場合、エラーが発生します。
  * 方向が正しく指定されていない場合、エラーが発生します。
  * 関数が条件関数として適切でなく、引数が間違っている場合、エラーが発生します。

# 例

```julia-repl
julia> velocity_bc!(t -> 2.0, body, :all_points, 1)

julia> velocity_bc!((p,t) -> p[1] * t, body, :all_points, :y)

julia> velocity_bc!(t -> t > 0.00001 ? 1.0 : NaN, body, :all_points, :z)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  3 boundary condition(s):
    BC on velocity: point_set=all_points, dim=1
    BC on velocity: point_set=all_points, dim=3
    Pos.-dep. BC on velocity: point_set=all_points, dim=2
```

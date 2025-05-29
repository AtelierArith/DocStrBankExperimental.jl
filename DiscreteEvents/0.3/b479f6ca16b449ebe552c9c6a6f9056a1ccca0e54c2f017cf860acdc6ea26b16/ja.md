```
event!([clk], ex, cond; <キーワード引数>)
```

`ex`を条件付きイベントとしてスケジュールし、条件`cond`は各クロックティックで評価されます。

# 引数

  * `clk<:AbstractClock`: クロックが供給されていない場合、イベントは𝐶にスケジュールされます。
  * `ex<:Action`: 式または関数、またはそれらのタプル。
  * `cond<:Action`: すべての関数または式が真を返す場合、条件は真です。

# キーワード引数

  * `cid::Int=clk.id`: cid ≠ clk.idの場合、イベントをid == cidの並列クロックに割り当てます。これは`spawn`を上書きします。
  * `spawn::Bool=false`: trueの場合、他の利用可能なスレッドでイベントを生成します。

# 例

```jldoctest
julia> using DiscreteEvents

julia> c = Clock()   # 新しいクロックを作成
Clock 1: state=:idle, t=0.0, Δt=0.01, prc:0
  scheduled ev:0, cev:0, sampl:0

julia> event!(c, fun((x)->println(tau(x), ": now I'm triggered"), c), fun(>=, fun(tau, c), 5))

julia> run!(c, 10)   # サンプリングは正確ではないため、イベントを発火させるのに502サンプルステップかかります
5.009999999999938: now I'm triggered
"run! finished with 0 clock events, 502 sample steps, simulation time: 10.0"
```

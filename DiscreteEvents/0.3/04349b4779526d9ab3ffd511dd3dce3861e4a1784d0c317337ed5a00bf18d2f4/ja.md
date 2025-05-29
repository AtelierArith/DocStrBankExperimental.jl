```
event!([clk], ex, t; <キーワード引数>)
event!([clk], ex, t, cy; <キーワード引数>)
event!([clk], ex, T, t; <キーワード引数>)

指定された時間 `t` にイベントをスケジュールします。

`t` が `Distribution` の場合、イベント時間は `rand(t)` として評価されます。`cy` が `Distribution` の場合、イベントはランダムな間隔 `rand(cy)` の後に繰り返されます。評価された時間が ≤ clk.time の場合、イベントは `clk.time` にスケジュールされます。

# 引数

  * `clk<:AbstractClock`: クロック。指定されていない場合、イベントは 𝐶 にスケジュールされます。
  * `ex<:Action`: 式または関数、またはそれらのタプル。
  * `T::Timing`: タイミング。`at`、`after`、または `every` のいずれか。
  * `t`: イベント時間。`Number` または `Distribution`。
  * `cy`: 繰り返しサイクル。`Number` または `Distribution`。

# キーワード引数

  * `n::Int=typemax(Int)`: 繰り返しイベントの数。
  * `cid::Int=clk.id`: `cid ≠ clk.id` の場合、イベントを id == cid の並列クロックに割り当てます。これは `spawn` を上書きします。
  * `spawn::Bool=false`: true の場合、他の利用可能なスレッドでイベントを生成します。

# 例

```

jldoctest julia> using DiscreteEvents, Distributions, Random

julia> Random.seed!(123);

julia> c = Clock() Clock 1: state=:idle, t=0.0, Δt=0.01, prc:0   scheduled ev:0, cev:0, sampl:0

julia> f(x) = x[1] += 1 f (generic function with 1 method)

julia> a = [0] 1-element Array{Int64,1}:  0

julia> event!(c, fun(f, a), 1)                     # 1番目のイベントは1で

julia> event!(c, fun(f, a), at, 2)                 # 2番目のイベントは2で

julia> event!(c, fun(f, a), after, 3)              # 3番目のイベントは3の後で

julia> event!(c, fun(f, a), every, Exponential(3)) # λ=1/3 のポアソン過程

julia> run!(c, 50) "run! finished with 26 clock events, 0 sample steps, simulation time: 50.0"

julia> a 1-element Array{Int64,1}:  26 ```

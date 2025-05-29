```
sample(rng, sim, n=1, input_mean=0; σₓ = nothing, split_long=false, randomise_values=true, Fvar=nothing, alt=false, poisson=false, exponentiate=false, error_size=0.02)
```

与えられたパワースペクトル密度（PSD）を使用して時系列を生成します。[1995A&A...300..707T](@cite) メソッドを使用します。

# 引数

  * `rng::MersenneTwister`: 擬似乱数生成器。
  * `sim::Simulation`: シミュレーション
  * `n::Int`: 生成する時系列の数。デフォルトは1。
  * `input_mean::Real`: 時系列の平均。デフォルトは0。
  * `σₓ::Array{Float64, 1}`: 時系列の誤差バー。デフォルトはnothing。
  * `split_long::Bool`: trueの場合、時系列は`sim.S_low`-1で与えられる短い時系列に分割されます。デフォルトはtrue。
  * `randomise_values::Bool`: trueの場合、時系列の値はランダム化されます。デフォルトはtrue。
  * `Fvar::Real`: 時系列の分散。デフォルトはnothing。
  * `alt::Bool`: trueの場合、代替のTimmer & Koenigメソッドを使用します。デフォルトはfalse。
  * `poisson::Bool`: trueの場合、ポアソンノイズが時系列に追加されます。デフォルトはfalse。
  * `exponentiate::Bool`: trueの場合、時系列は指数化されます。デフォルトはfalse。
  * `error_size::Real`: 誤差の大きさ。デフォルトは0.05。

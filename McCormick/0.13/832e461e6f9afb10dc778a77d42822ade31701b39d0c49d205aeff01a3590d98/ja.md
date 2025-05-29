```julia
struct MC{N, T<:McCormick.RelaxTag} <: Real
```

`MC{N, T <: RelaxTag} <: Real` は、標準的な計算をオーバーロードするために使用される McCormick (w/ (sub)gradient) 構造です。フィールドは次のとおりです：

  * `cv::Float64`: 凸緩和
  * `cc::Float64`: 凹緩和
  * `Intv::IntervalArithmetic.Interval{Float64}`: 区間境界
  * `cv_grad::StaticArraysCore.SVector{N, Float64} where N`: 凸緩和の (部分)勾配
  * `cc_grad::StaticArraysCore.SVector{N, Float64} where N`: 凹緩和の (部分)勾配
  * `cnst::Bool`: 緩和がドメイン全体で定数であるかどうかを示すブール値。区間/定数を境界付けている場合は真。そうでない場合は偽です。この値は計算の過程で変わる可能性があります。`zero(x)` の `cnst` は `true` ですが、`x.cnst` が `false` である場合もあります。

```
mutable struct Diagnostic{T, N} <: AbstractDiagnostic
```

`T`型の要素`N`個を含む診断。

  * `calc::Function`: `calc(prob)`を介して診断を返す関数
  * `prob::FourierFlows.Problem`: この診断に関連する問題
  * `data::Vector`: 診断の時系列が保存されるベクター
  * `t::Vector{Float64}`: 診断が保存された時刻のベクター
  * `steps::Vector{Int64}`: 診断が保存された問題の`step`のベクター
  * `freq::Int64`: 診断を保存する頻度（何回の`problem.step`ごとに）
  * `i::Int64`: `diagnostic.data`が更新された回数を示す整数

```
solve!(schedule::Schedule, timeout::Float64 = Inf, all_solutions::Bool = false)::Tuple{OrderedDict{String,String},MOI.TerminationStatusCode}
```

与えられたスケジュールをその場で解決し、`String=>String`の解決策とステータスコードを返します。

# 引数

  * `schedule::Schedule`: 問題を表すスケジュールオブジェクト。
  * `timeout::Float64=Inf`: モデルを実行する最大時間を表す浮動小数点数。
  * `all_solutions::Bool=false`: すべての解を返すか、最初の解のみを返すかを示すブール値。

# 注意事項

  * スケジュールは、ステータスコードが[`MOI.OPTIMAL`](https://jump.dev/JuMP.jl/stable/moi/reference/models/#MathOptInterface.TerminationStatusCode)の場合にのみ最適に解決されます。

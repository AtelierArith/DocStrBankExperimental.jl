```
generate(process::ContinuousTimeEmpiricalProcess, n; initial_condition=rand(1:size(process.cumulative_distribution)[1]))
```

連続時間経験的プロセス `process` から長さ `n` のマルコフ連鎖を生成します。

# 引数

  * `process::ContinuousTimeEmpiricalProcess`: マルコフ連鎖を生成するための連続時間経験的プロセス。
  * `n::Int`: 生成するジャンプの数。すなわち、マルコフ連鎖の長さの下限。
  * `initial_condition::Int=rand(1:size(process.cumulative_distribution)[1])`: マルコフ連鎖の初期条件。

# キーワード引数

  * `progress::Bool=false`: 進行状況バーを表示するかどうか。

# 戻り値

  * `Vector{Int}`: 連続時間経験的 `process` によって生成されたマルコフ連鎖。

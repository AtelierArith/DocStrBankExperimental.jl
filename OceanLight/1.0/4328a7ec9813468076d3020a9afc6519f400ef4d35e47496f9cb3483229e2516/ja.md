```
setwave!(η::Array{<:Float64,2},ηx::Array{<:Float64,2},ηy::Array{<:Float64,2},rms::Float64,p::Param)
```

既存の波面分布グリッドに値を与える

# 引数

  * `η::Array{<:Float64,2}`: 水面の標高。
  * `ηx::Array{<:Float64,2}`: x方向の水面の標高の偏微分。
  * `ηy::Array{<:Float64,2}`: y方向の水面の標高の偏微分。
  * `rms::Float64`: ランダム数。
  * `p::Param`: シミュレーションパラメータ。

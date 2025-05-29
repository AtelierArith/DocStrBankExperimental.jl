```
interface!(xpb::Array{<:Float64,2},ypb::Array{<:Float64,2},zpb::Array{<:Float64,2},
                θ::Array{<:Float64,2},ϕ::Array{<:Float64,2},fres::Array{<:Float64,2},
                η::Array{<:Float64,2},ηx::Array{<:Float64,2},ηy::Array{<:Float64,2},p::Param)
```

大気から水中に伝わる光子または光線の反射と屈折を計算します。

# 引数

  * `xpb::Array{<:Float64,2}`: 光子の初期x座標。
  * `ypb::Array{<:Float64,2}`: 光子の初期y座標。
  * `zpb::Array{<:Float64,2}`: 光子の初期z座標。
  * `θ::Array{<:Float64,2}`: z軸に対する光線の角度：極角。
  * `ϕ::Array{<:Float64,2}`: x軸に対する光線の角度：方位角。
  * `fres::Array{<:Float64,2}`: 偏光されていない光のフレネル係数または分数透過率。
  * `η::Array{<:Float64,2}`: 水面の標高。
  * `ηx::Array{<:Float64,2}`: x方向の水面の標高の偏微分。
  * `ηy::Array{<:Float64,2}`: y方向の水面の標高の偏微分。
  * `p::Param`: シミュレーションパラメータ。

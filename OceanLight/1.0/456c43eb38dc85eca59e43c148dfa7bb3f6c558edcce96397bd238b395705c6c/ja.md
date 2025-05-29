```
transfer!(ed1d::Array{<:Float64,1},edi::Array{<:Int64,1},edj::Array{<:Int64,1},
               edk::Array{<:Int64,1},count::Array{<:Int64,1},esol::Array{<:Float64,2},θ::Float64,ϕ::Float64,fres::Float64,
               ip::Int64,xpb::Float64,ypb::Float64,zpb::Float64,randrng,η::Array{<:Float64,2},
               ph::Array{<:Float64,1},θps::Array{<:Float64,1},p::Param,mode=0::Int64)
```

モンテカルロシミュレーションを実行します。

# 引数

  * `ed1d::Array{<:Float64,1}`: 光子が着地するグリッドの4つのコーナーに割り当てられる照度の割合
  * `edi::Array{<:Int64,1}`: 光子が着地する単一のグリッドのx座標（グリッド番号）：左下、右下、左上、右上から。
  * `edj::Array{<:Int64,1}`: 光子が着地する単一のグリッドのy座標（グリッド番号）：左下、右下、左上、右上から。
  * `edk::Array{<:Int64,1}`: 光子が移動するエネルギーレイヤーの番号、1 by 4配列の最上部ztopから
  * `count::Array{<:Int64,1}`: （並列計算）ed1d、edi、edj、edkのサイズを追跡するための1から4までのダミー整数スパン。
  * `esol::Array{<:Float64,2}`: `solar`モードのための照度解グリッド（開発中）
  * `θ::Float64`: z軸に対する光線の角度：極角。
  * `ϕ::Float64`: x軸に対する光線の角度：方位角。
  * `fres::Float64`: フレネル係数または非偏光光のための分数透過率。
  * `ip::Int64`: シミュレーション中の現在の光子の番号（すなわち、ip ∈ {1, 2,..., nphoton}）
  * `xpb::Float64`: 光子の初期x座標。
  * `ypb::Float64`: 光子の初期y座標。
  * `zpb::Float64`: 光子の初期z座標。
  * `randrng`: RandomパッケージによってエクスポートされたPRNG（擬似乱数生成器）
  * `η::Array{<:Float64,2}`: 水面の標高。
  * `ph::Array{<:Float64,1}`: 散乱角の累積分布（`phasePetzold()`から取得）
  * `θps::Array{<:Float64,1}`: 散乱前の光子の方向に対する新しい軌道との間の角度、各`ϕps`に対応（`phasePetzold()`から取得）
  * `p::Param`: シミュレーションパラメータ。
  * `mode::Int64`: 異なる照度計算のモード（開発中）

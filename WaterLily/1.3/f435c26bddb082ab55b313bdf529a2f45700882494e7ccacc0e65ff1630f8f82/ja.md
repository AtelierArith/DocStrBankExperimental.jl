```
Simulation(dims::NTuple, u_BC::Union{NTuple,Function}, L::Number;
           U=norm2(u_BC), Δt=0.25, ν=0., ϵ=1, perdir=()
           uλ::nothing, g=nothing, exitBC=false,
           body::AbstractBody=NoBody(),
           T=Float32, mem=Array)
```

WaterLily.jlシミュレーションのコンストラクタ:

  * `dims`: シミュレーションドメインの次元。
  * `u_BC`: シミュレーションドメインの速度境界条件。タプル `u_BC[i]=uᵢ, i=eachindex(dims)` または時間変化関数 `f(i,t)` のいずれか。
  * `L`: シミュレーションの長さスケール。
  * `U`: シミュレーションの速度スケール。
  * `Δt`: 初期時間ステップ。
  * `ν`: スケールされた粘度 (`Re=UL/ν`)。
  * `g`: ドメイン加速度、`g(i,t)=duᵢ/dt`
  * `ϵ`: BDIMカーネル幅。
  * `perdir`: `(i,)`方向のドメイン周期境界条件。
  * `exitBC`: `i=1`方向の対流出口境界条件。
  * `uλ`: 初期速度場を生成する関数。
  * `body`: 浸漬幾何。
  * `T`: 配列要素の型。
  * `mem`: メモリ位置。`Array`、`CuArray`、`ROCm`はそれぞれCPU、NVIDIA、またはAMDデバイスで実行するためのもの。

例については`examples`フォルダ内のファイルを参照してください。

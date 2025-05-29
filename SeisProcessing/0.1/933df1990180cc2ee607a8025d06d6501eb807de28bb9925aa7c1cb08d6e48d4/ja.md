```
SeisSincInterp1D(d,order)
```

1D sinc 補間を介して地震トレースを再サンプリングします。時系列は毎 dt 秒ごとにサンプリングされ、出力は dt/`order` の時間間隔を持つ系列に対応します。

# 引数

  * `d::Array{Real,N}`: N 次元データ、最初の次元は時間
  * `order::Integer`: 補間の次数 2,4

# 例

波形の2倍アップサンプリング

```julia
julia> order = 2; dt=0.004; w = Ricker(dt=dt, f0=20); t = collect(0:1:length(w)-1)*dt;
julia> wout = SeisSincInterp1D(w,order); tout = collect(0:1:length(wout)-1)*dt/order;
julia> plot(t,w); plot(tout,wout,"*")
```

集めの4倍アップサンプリング

```julia
julia> d = SeisLinearEvents(); di = SeisSincInterp1D(d,4);
julia>  SeisPlotTX(d,style="wiggles")
julia>  SeisPlotTX(di,style="wiggles")  
```

2018年5月、MDS ```

```
plot_twophoton!(ax,twophotonstate::TwophotonView,times;kwargs...)
plot_twophoton!(ax,twophotonstate::TwoWaveguideView,times;kwargs...)
plot_twophoton!(ax,state::Ket,times;kwargs...)
plot_twophoton!(ax,twophotonstate,times;kwargs...)
```

与えられた ax に二光子状態をプロットします。

# 引数

  * `PyPlot` からのタイプ PyObject <AxesSubplot: > の ax
  * プロットされる状態 twophotonstate または state。state が `Ket` の場合は [`TwoPhotonView`](@ref) が呼び出されて twophotonstate を抽出します。そうでない場合、twophotonstate は次元 (length(times),length(times)) の AbstractArray である必要があります。

# プロットされた状態を持つ ax.contour オブジェクトを返します。

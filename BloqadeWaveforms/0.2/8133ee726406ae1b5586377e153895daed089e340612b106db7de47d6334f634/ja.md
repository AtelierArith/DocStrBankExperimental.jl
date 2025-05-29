```
smooth([kernel=Kernel.gaussian], f; edge_pad_size::Int=length(f.clocks))
```

カーネルスムーザー関数は、加重移動平均法を介して区分線形関数/波形に対して使用されます。

# 引数

  * `kernel`: カーネル関数、デフォルトは [`Kernels.gaussian`](@ref) です。
  * `f`: [`Union{PiecewiseLinear, PiecewiseConstant}`](@ref) 関数または [`Waveform{<:Union{PiecewiseLinear, PiecewiseConstant}}`](@ref) です。

# キーワード引数

  * `kernel_radius`: カーネルの半径。
  * `edge_pad_size`: エッジパディングのサイズ。

```
residuals(sp; kwargs...)
```

最適なパラメータの周りまたは指定されたパラメータ空間に対して、`ScalingProblem`の残差を計算します。

# 引数

  * `sp::ScalingProblem`: 残差を計算するための`ScalingProblem`。

# キーワード引数

  * `p_space::Vector{Vector{Float64}}`: 残差を計算するためのパラメータ空間。提供されない場合、最適なパラメータ、その誤差、およびステップ数からパラメータ空間が計算されます。
  * `N_steps::Int=50`: デフォルトのパラメータ空間に使用するステップ数。
  * `dims::Vector{Int}=[1, ...]`: 残差を計算する次元。指定されない場合、すべての次元が使用されます。

# 戻り値

  * `p_space::Vector{StepRangeLen}`: 計算に使用されるパラメータ空間。
  * `residuals::Array{Float64}`: 指定されたパラメータ空間の残差。

# 例

```julia
# 例えば、xs、ys、Lsはイジングモデルの感受性のデータだとしましょう
using ScalingCollapse
sp = ScalingProblem(xs, ys, Ls;
    sc=ScalingFunction(:xny; p_names=["T_c", "nu", "gamma"]),
    dx=[-1.0, 2.0],
)

# 最適なパラメータの周りの残差の風景を次のように計算できます：
p_space, residuals = residuals(sp)
# 上記のケースでは length(p_space) == 3 で size(residuals) == (50, 50, 50)

# 興味のある次元を次のように指定できます：
p_space, residuals = residuals(sp; dims=[1, 2])
# これで length(p_space) == 2 で size(residuals) == (50, 50)
# 第三のパラメータ（この場合はgamma）を最適値に固定し、
# 3D残差の風景を通る2Dカットを計算しました
```

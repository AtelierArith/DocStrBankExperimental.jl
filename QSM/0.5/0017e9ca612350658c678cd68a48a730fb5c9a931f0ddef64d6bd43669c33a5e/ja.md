```
smv_kernel(sz, vsz, r; kwargs...) =
    smv_kernel(Float64, sz, vsz, r; kwargs...)

smv_kernel(
    ::Type{T<:AbstractFloat},
    sz::NTuple{3, Integer},
    vsz::NTuple{3, Real}
    r::Real;
    transform::Union{Nothing, Symbol} = nothing,
    shift::Bool = false
) -> Array{T, 3}
```

球面平均値カーネル (SMV)。

### 引数

  * `sz::NTuple{3, Integer}`: 配列サイズ
  * `vsz::NTuple{3, Real}`: ボクセルサイズ
  * `r::Real`: `vsz` の単位での球の半径

### キーワード

  * `transform::Union{Nothing, Symbol} = nothing`:   SMVカーネルを変換 `(:rfft, :fft)`
  * `shift::Bool = false`:

      * `transform = nothing`:   球が `N÷2+1` (`false`) または `(1,1,1)` (`true`) に中心
      * `transform ∈ (:rfft, :fft)`:   球が `(1,1,1)` (`false`) または `N÷2+1` (`true`) に中心

### 戻り値

  * `Array{T, 3}`: SMVカーネル

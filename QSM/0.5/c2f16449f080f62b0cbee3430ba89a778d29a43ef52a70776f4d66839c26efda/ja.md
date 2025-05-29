```
laplace_kernel(vsz) =
    laplace_kernel(Float64, vsz)

laplace_kernel(sz, vsz; kwargs...) =
    laplace_kernel(Float64, sz, vsz; kwargs...)

laplace_kernel(::Type{T<:AbstractFloat}, vsz::NTuple{3, Real}) =
    laplace_kernel(T, (3, 3, 3), vsz, transform=nothing, shift=false)

laplace_kernel(
    ::Type{T<:AbstractFloat},
    sz::NTuple{3, Integer},
    vsz::NTuple{3, Real};
    negative::Bool = false,
    transform::Union{Nothing, Symbol} = nothing,
    shift::Bool = false
) -> Array{T, 3}
```

離散7点ステンシルラプラシアンカーネル。

### 引数

  * `sz::NTuple{3, Integer}`: 配列サイズ
  * `vsz::NTuple{3, Real}`: ボクセルサイズ

### キーワード

  * `negative::Bool = false`: 負のラプラシアンを構築する (`true`)
  * `transform::Union{Nothing, Symbol} = nothing`:   ラプラシアンカーネルを変換する `(:rfft, :fft)`
  * `shift::Bool = false`:

      * `transform = nothing`:   中心が `N÷2+1` の球 (`false`) または `(1,1,1)` の球 (`true`)
      * `transform ∈ (:rfft, :fft)`:   中心が `(1,1,1)` の球 (`false`) または `N÷2+1` の球 (`true`)

### 戻り値

  * `Array{T, 3}`: ラプラシアンカーネル

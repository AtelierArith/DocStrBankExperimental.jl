```
ns_idwt(nxw, wt, [L])
```

1D信号に対する逆非標準ウェーブレット変換。

# 引数

  * `nxw::AbstractVector{T} where T<:AbstractFloat`: 長さ $2^{J+1}$ の非標準ウェーブレット変換された1D信号。
  * `wt::OrthoFilter`: ウェーブレットフィルターのタイプ。
  * `L::Integer`: (デフォルト: `maxtransformlevels(nxw) - 1`) 分解レベルの数。

# 戻り値

  * `x::Vector{T}`: 長さ $2^J$ の1D信号。

# 例

```jldoctest
julia> using Wavelets, WaveletsExt; import Random: seed!

julia> seed!(1234); x = randn(4)
4-element Vector{Float64}:
 -0.3597289068234817
  1.0872084924285859
 -0.4195896169388487
  0.7189099374659392

julia> wt = wavelet(WT.haar);

julia> nxw = ns_dwt(x, wt)      # 非標準変換
8-element Vector{Float64}:
  0.0
  0.0
  0.5133999530660974
 -0.2140796325390069
  0.5144057481561487
  0.21165142839163664
  1.0231392469635638
  0.8050407552974883

julia> x̂ = ns_idwt(nxw, wt)     # 非標準逆変換
4-element Vector{Float64}:
  0.004010885979070622
  1.4509482852311382
 -0.2699294566753035
  0.8685700977294846

julia> x ≈ x̂                    # 標準dwtとは異なり、x ≠ x̂
false
```

**参照:** [`nonstd_wavemult`](@ref), [`mat2sparseform_nonstd`](@ref), [`ns_dwt`](@ref), [`ndyad`](@ref)

```
nonstd_wavemult(M, x, wt, [L], [ϵ])
nonstd_wavemult(NM, x, wt, [L])
```

`M`が$n$ by $n$行列である場合、$y = Mx$を計算する方法は2つあります。最初の方法は、標準の行列乗算を使用して積を計算することです。このアルゴリズムは、$O(n^2)$のオーダーで動作し、ここで$n$は`x`の長さです。

2番目の方法は、行列とベクトルの両方を非標準形式に変換し、非標準形式を掛け算することです。行列が非標準形式でスパースである場合、これは$O(n)$のオーダーのアルゴリズムになる可能性があります。

!!! tip
    元の行列`M`を入力として使用することを選択することができます。`nonstd_wavemult(M, x, wt, [L], [ϵ])`を実行することで。ただし、非標準形式のスパース行列`NM`が事前に計算されている場合、`nonstd_wavemult(NM, x, wt, [L])`を実行することで冗長なステップをスキップできます。


# 引数

  * `M::AbstractVector{T} where T<:AbstractFloat`: $n$ by $n$行列。
  * `NM::SparseMatrixCSC{T,S} where {T<:AbstractFloat, S<:Integer}`: `M`の非標準変換スパース行列。
  * `x::AbstractVector{T} where T<:AbstractFloat`: 自然基底における長さ$n$のベクトル。
  * `wt::OrthoFilter`: ウェーブレットフィルタのタイプ。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 分解レベルの数。
  * `ϵ::T where T<:AbstractFloat`: (デフォルト: `1e-4`) `M`の非標準変換のための切断基準。

# 戻り値

  * `y::Vector{T}`: $Mx$の標準近似。

# 例

```jldoctest
julia> using Wavelets, WaveletsExt

julia> M = randn(4,4); x = randn(4); wt = wavelet(WT.haar);

julia> NM = mat2sparseform_nonstd(M, wt); y₀ = nonstd_wavemult(NM, x, wt)
4-element Vector{Float64}:
 -1.2590015844047044
 -1.3234024176418535
  2.1158027198405627
  1.5364835417087566

julia> y₁ = nonstd_wavemult(M, x, wt)
4-element Vector{Float64}:
 -1.2590015844047044
 -1.3234024176418535
  2.1158027198405627
  1.5364835417087566

julia> y₀ == y₁                     # 両方の方法は同等です
true
```

**参照:* [`std_wavemult`](@ref), [`mat2sparseform_nonstd`](@ref), [`ns_dwt`](@ref), [`ns_idwt`](@ref) 

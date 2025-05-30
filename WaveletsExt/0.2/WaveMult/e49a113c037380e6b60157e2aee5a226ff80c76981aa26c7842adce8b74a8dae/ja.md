```
std_wavemult(M, x, wt, [L], [ϵ])
std_wavemult(SM, x, wt, [L])
```

`M`が$n$ by $n$行列である場合、$y = Mx$を計算する方法は2つあります。最初の方法は、標準の行列乗算を使用して積を計算することです。このアルゴリズムは、$O(n^2)$のオーダーで動作し、ここで$n$は`x`の長さです。

2番目の方法は、行列とベクトルの両方を標準形式に変換し、標準形式を掛け算することです。行列が標準形式でスパースである場合、これは$O(n)$のオーダーのアルゴリズムになる可能性があります。

!!! tip
    元の行列`M`を入力として使用することを選択することもできます。`std_wavemult(M, x, wt, [L], [ϵ])`を実行することで。ただし、標準形式のスパース行列`SM`が事前に計算されている場合、`std_wavemult(SM, x, wt, [L])`を実行することで冗長なステップをスキップできます。


# 引数

  * `M::AbstractVector{T} where T<:AbstractFloat`: $n$ by $n$行列。
  * `NM::SparseMatrixCSC{T,S} where {T<:AbstractFloat, S<:Integer}`: `M`の標準変換スパース行列。
  * `x::AbstractVector{T} where T<:AbstractFloat`: 自然基底の長さ$n$のベクトル。
  * `wt::OrthoFilter`: ウェーブレットフィルタのタイプ。
  * `L::Integer`: (デフォルト: `maxtransformlevels(x)`) 分解レベルの数。
  * `ϵ::T where T<:AbstractFloat`: (デフォルト: `1e-4`) `M`の標準変換のための切り捨て基準。

# 戻り値

  * `y::Vector{T}`: $Mx$の標準形式近似。

# 例

```jldoctest
julia> using Wavelets, WaveletsExt

julia> M = randn(4,4); x = randn(4); wt = wavelet(WT.haar);

julia> SM = mat2sparseform_std(M, wt); y₀ = std_wavemult(SM, x, wt)
4-element Vector{Float64}:
  2.2303830532617344
 -0.12704611958926648
  2.656411941014368
 -4.811388406857621

julia> y₁ = std_wavemult(M, x, wt)
4-element Vector{Float64}:
  2.2303830532617344
 -0.12704611958926648
  2.656411941014368
 -4.811388406857621

julia> y₀ == y₁
true
```

**参照:** [`nonstd_wavemult`](@ref), [`mat2sparseform_std`](@ref)

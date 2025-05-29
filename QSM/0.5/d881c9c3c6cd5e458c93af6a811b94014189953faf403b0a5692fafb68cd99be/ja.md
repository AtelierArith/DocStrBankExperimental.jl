```
homodyne(
    u::AbstractArray{<:Complex{<:AbstractFloat}, N > 1},
    wsz::Union{Integer, NTuple{2, Integer}},
    window::Symbol,
    args...
) -> typeof(similar(u))

homodyne!(
    u::AbstractArray{<:Complex{<:AbstractFloat}, N > 1},
    wsz::Union{Integer, NTuple{2, Integer}},
    window::Symbol,
    args...
) -> u

homodyne!(
    v::AbstractArray{<:Complex{<:AbstractFloat}, N > 1},
    u::AbstractArray{<:Complex{<:AbstractFloat}, N},
    wsz::Union{Integer, NTuple{2, Integer}},
    window::Symbol,
    args...
) -> v
```

ホモダインフィルター。

複素データのk空間に2dウィンドウを適用してフィルタリングします: `u / F^-1(w * F(u))`。

### 引数

  * `u::AbstractArray{<:Complex{<:AbstractFloat}, N > 1}`:   複素（マルチエコー）データ
  * `wsz::Union{Integer, NTuple{2, Integer}}`: ウィンドウサイズ
  * `window::Symbol`: ウィンドウ関数

      * `:fermi`: `w = 1 / (1 + exp((x-radius) / width)), x ∈ [-0.5, 0.5]`
      * `:gaussian`: `w = exp(-0.5*(x/σ)^2), x ∈ [-0.5, 0.5]`
      * `:hamming`: `w = 0.54 + 0.46*cos(2π*x), x ∈ [-0.5, 0.5]`
      * `:hann`: `w = 0.5*(1 + cos(2π*x)), x ∈ [-0.5, 0.5]`
  * `args...`:

      * `window == :fermi`: `radius::Real, width::Real`
      * `window == :gaussian`: `σ::Real`
      * それ以外: 未使用

### 戻り値

  * `typeof(similar(u)) / u / v`: ホモダインフィルタリングされた複素（マルチエコー）データ

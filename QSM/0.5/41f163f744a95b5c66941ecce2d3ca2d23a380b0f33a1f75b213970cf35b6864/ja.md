```
makewindow(
    sz::NTuple{2, Integer},
    wsz::Union{Integer, NTuple{2, Integer}},
    window::Symbol,
    args...
) -> Array{Float64, 2}
```

2次元k空間ウィンドウ。

ウィンドウはインデックス `(1,1)` に中心を置いています。この関数はDSP.jlの `makewindow(window, n = wsz, padding = sz - wsz, zerophase=true)` のラッパーです。

### 引数

  * `sz::NTuple{2, Integer}`: 配列サイズ
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

  * `Array{Float64, 2}:` ウィンドウ

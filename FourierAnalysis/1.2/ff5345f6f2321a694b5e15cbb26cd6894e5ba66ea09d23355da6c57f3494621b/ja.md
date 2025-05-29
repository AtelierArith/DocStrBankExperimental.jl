```julia
function fdf(sr :: Int,
             wl :: Int;
          DC :: Bool = false)
```

サンプリングレート `sr` とウィンドウ長 `wl` に対して、実数FFTのすべての**F**ーリエ**d**離散**f**周波数を持つベクトルを返します。`DC` が false の場合、最初の離散周波数はビン（位置）1から始まり、ベクトルの長さは $wl÷2$（整数除算）です。そうでない場合、DCレベルは位置1にあり、ベクトルの長さは $(wl÷2)+1$ です。

**関連情報**: [`f2b`](@ref), [`fres`](@ref), [`b2f`](@ref), [`brange`](@ref).

**例**:

```julia
using FourierAnalysis
fdf(8, 16)
# return the 8-element Array{Float64,1}:
# [0.5, 1.0, 1.5, 2.0, 2.5, 3, 3.5, 4.0]
```

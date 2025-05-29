```julia
function brange(wl :: Int;
             DC :: Bool = false)
```

ウィンドウ長 `wl` に対してすべてのフーリエ離散周波数をカバーする実FFTベクトルのビンの範囲を返します。

`DC` が false の場合、範囲は $1:(wl÷2)$（整数除算）です。それ以外の場合は $1:(wl÷2)+1$ です。

**参照**: [`f2b`](@ref), [`fres`](@ref), [`b2f`](@ref), [`fdf`](@ref)。

**例**:

```julia
using FourierAnalysis
brange(0.5, 8) # return 1:4
```

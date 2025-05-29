```julia
function fres(sr :: Int,
              wl :: Int)
```

FFT **周波数** **解像度** はサンプリングレート `sr` とウィンドウ長 `wl` に基づいています。

**関連情報**: [`f2b`](@ref), [`b2f`](@ref), [`fdf`](@ref), [`brange`](@ref).

**例**:

```julia
using FourierAnalysis
fres(1024, 2048) # return 0.5
```

```julia
function bbands(sr :: Int,
                wl :: Int,
         bandwidth :: IntOrReal;
    DC :: Bool = false)
```

離散フーリエ周波数のビンで、$wl÷2$（整数除算）までの実FFTのすべての`bandwidth`間隔のバンドパス領域の限界を保持する整数のベクトルを返します。

これは関数[`bands`](@ref)によって使用されます。

これらのビンに対応するHzの周波数を知るには、[`fbands`](@ref)を呼び出してください。

**参照**: [`bands`](@ref)。

**関連**: [`fbands`](@ref)。

**例**:

```julia
using FourierAnalysis
bbands(128, 256, 16) # return [1, 32, 64, 96, 128]
fbands(128, 256, 16) # return [0.5, 16.0, 32.0, 48.0, 64.0]

bbands(128, 256, 16; DC=true) # return [2, 33, 65, 97, 129]
fbands(128, 256, 16; DC=true) # return [0.5, 16.0, 32.0, 48.0, 64.0]

bbands(128, 128, 16) # return [1, 16, 32, 48, 64]
fbands(128, 128, 16) # return [1.0, 16.0, 32.0, 48.0, 64.0]
```

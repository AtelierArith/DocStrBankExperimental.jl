```julia
function b2f(bin :: Int,
              sr :: Int,
              wl :: Int;
        DC :: Bool = false)
```

**b**in **to f**requency. 返す最も近い離散フーリエ周波数（Hz）で、実FFTベクトルのビン（位置）に対応し、サンプリングレート `sr` とウィンドウ長 `wl` が与えられます。FFTベクトルは、常にJuliaでのように1ベースであると仮定されます。

`DC` が false の場合、最初の離散周波数はビン1にあると仮定されます。そうでない場合、DCレベルはビン1にあり、最初の離散周波数はビン2にあると仮定されます。

**参照**: [`f2b`](@ref), [`fres`](@ref), [`fdf`](@ref), [`brange`](@ref).

**例**:

```julia
using FourierAnalysis
f2b(20, 512, 1024) # return 40
f2b(10, 128, 128) # return 10
```

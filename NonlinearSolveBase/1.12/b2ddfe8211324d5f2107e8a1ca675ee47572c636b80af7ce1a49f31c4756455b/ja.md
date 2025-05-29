```
Dogleg(; linsolve = nothing)
```

信頼領域のサイズに応じて、ニュートン法と最急降下法の間で切り替えます。信頼領域は、`solve!`へのキーワード引数`trust_region`を介して指定されます。

関連情報として、[`SteepestDescent`](@ref)、[`NewtonDescent`](@ref)、[`DampedNewtonDescent`](@ref)を参照してください。

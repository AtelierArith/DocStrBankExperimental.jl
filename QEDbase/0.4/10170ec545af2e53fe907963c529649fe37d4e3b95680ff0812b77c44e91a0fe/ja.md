```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, species::AbstractParticleType, n::Int)
```

与えられた [`AbstractPhaseSpacePoint`](@ref) において、方向 `dir` と種 `species` を持つ `n` 番目の粒子の運動量を返します。`n` がこの位相空間点の有効範囲外である場合、`BoundsError` がスローされます。

!!! note
    この関数は n を `Int` 値として受け取ります。もし `n` がコンパイル時定数（例えば、リテラル `1` または `2`）である場合、オーバーヘッドのないバージョンのこの関数を呼び出すために `Val(n)` を代わりに使用できます。


```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, species::AbstractParticleType, n::Val{N})
```

与えられた [`AbstractPhaseSpacePoint`](@ref) の `n` 番目の粒子の運動量を返します。この粒子は方向 `dir` と種 `species` を持ちます。もし `n` がこの位相空間点の有効範囲外であれば、`BoundsError` がスローされます。

!!! note
    この関数は `n` を `Val{N}` 型として受け取ります。つまり、コンパイル時定数値（例えばリテラル `1` や `2`）です。これにより、この関数はオーバーヘッドをゼロにすることができますが、**N** が実際にコンパイル時に知られている場合に限ります。そうでない場合は、`n::Int` を使用するこの関数のオーバーロードを使用してください。その関数は、`Val(n)` を使ってこの関数を呼び出すよりも速くなります。


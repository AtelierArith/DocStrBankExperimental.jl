```julia
(1)
function isUnwrapped(ϴ::TFPhase)

(2)
function isUnwrapped(𝚯::TFPhaseVector)
```

(1) TFPhaseオブジェクトϴの位相がアンラップされている場合はtrueを返します。

(2) 𝚯内のすべてのTFPhaseオブジェクトの位相がアンラップされている場合はtrueを返します。

**参照**: [`unwrapPhase`](@ref), [TFPhase](@ref), [TFPhaseVector](@ref).

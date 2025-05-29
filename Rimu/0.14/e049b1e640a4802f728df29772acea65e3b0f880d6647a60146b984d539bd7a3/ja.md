```
Projector(name=projector) <: PostStepStrategy
```

各ステップの後に、`dot(projector, dv)`を計算し、それを`DataFrame`の`name`の下に報告します。`projector`は[`AbstractDVec`](@ref)または[`AbstractProjector`](@ref)である可能性があります。

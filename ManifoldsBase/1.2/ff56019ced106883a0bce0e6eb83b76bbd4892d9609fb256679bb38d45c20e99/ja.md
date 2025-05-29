```
AbstractTangentVector = AbstractFibreVector{TangentSpaceType}
```

多様体の接ベクトルの型。[`AbstractManifold`](@ref)は必ずしもこの型を必要としませんが、例えば`Vector`や`Matrix`型の要素に対して実装される場合、この型はより複雑な表現、意味的検証、または多様体上の接ベクトルとその型の異なる表現のためのディスパッチに使用できます。

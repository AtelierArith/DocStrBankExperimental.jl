```
AbstractCotangentVector = AbstractFibreVector{CotangentSpaceType}
```

多様体のコタンジェントベクトルの型。[`AbstractManifold`](@ref) は必ずしもこの型を必要としませんが、例えば `Vector` や `Matrix` 型の要素に対して実装される場合、この型はより複雑な表現、意味的検証、または多様体上のコタンジェントベクトルとその型の異なる表現に対するディスパッチに使用できます。

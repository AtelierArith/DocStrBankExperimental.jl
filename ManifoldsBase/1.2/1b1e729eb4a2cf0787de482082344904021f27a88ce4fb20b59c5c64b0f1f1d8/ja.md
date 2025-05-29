```
AbstractManifoldPoint
```

多様体上の点のための型。[`AbstractManifold`](@ref) はこの型を必ずしも必要としませんが、例えば `Vector` や `Matrix` 型の要素に対して実装される場合、この型は次のように使用できます。

  * より複雑な表現のために、
  * 意味的検証のために、または
  * 多様体上の点の異なる表現に基づいてディスパッチするために。

意味的検証や異なる表現は通常、内部的に行列を格納するだけである可能性があるため、[`@manifold_element_forwards`](@ref) および [`@default_manifold_fallbacks`](@ref) を使用して実装のオーバーヘッドを削減することが可能です。

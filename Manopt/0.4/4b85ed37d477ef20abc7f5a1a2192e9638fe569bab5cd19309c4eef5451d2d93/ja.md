```
get_iterate(O::AbstractManoptSolverState)
```

[`AbstractManoptSolverState`](@ref)``s`内の（最後に保存された）反復を返します。これは通常、ソルバーが作業している多様体上の単一の点を指します。

デフォルトでは、これにより事前に状態のすべてのデコレーターも削除されます。

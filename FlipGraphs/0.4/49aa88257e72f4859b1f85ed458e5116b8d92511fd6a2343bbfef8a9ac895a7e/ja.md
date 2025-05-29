```
is_isomorphic(candidate::FGVertexCandidate, fgv::FGVertex; kwargs...) -> Bool
```

`candidate`が`fgv`の同変類にある場合は`true`を返します。

# 引数

  * `labeled_points :: Bool = true` : `false`に設定されている場合、同型は点の再ラベリングも許可します。

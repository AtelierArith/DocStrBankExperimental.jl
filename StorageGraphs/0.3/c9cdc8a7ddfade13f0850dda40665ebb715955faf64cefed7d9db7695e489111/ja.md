```
final_neighborhs(g, dep::Pair; dir=:out)
```

依存関係チェーンの末端にある隣接点の頂点インデックスを返します。注意: これは依存関係チェーンが有効であること（すべてのノードが存在すること）を前提としています。

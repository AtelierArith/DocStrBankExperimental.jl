```
SurfaceScalarCache(g::PhysicalGrid[,scaling=IndexScaling])
```

スカラーグリッドデータを持つ `BasicILMCache` タイプのキャッシュを作成します。これは、`g` で指定されたグリッドを使用し、浸漬点はありません。キーワード `scaling` は、操作のスケーリングを設定するために使用できます。デフォルトでは、これは `IndexScaling` に設定されており、微分演算子は差分演算子のみになります。`scaling = GridScaling` を使用すると、グリッドと間隔が考慮され、微分演算子はこの間隔によってスケーリングされます。キーワード `phys_params` は、物理パラメータを提供するために使用できます。

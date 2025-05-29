```
BVH(gbox, nodes, tris, ids)
```

三角メッシュの周りにバウンディングボリュームヒエラルキーを構築して、レイトレーサーを加速します。これは、対応する `rule` と組み合わせて `RayTracer` 関数の引数 `acceleration` に割り当てる必要があります。

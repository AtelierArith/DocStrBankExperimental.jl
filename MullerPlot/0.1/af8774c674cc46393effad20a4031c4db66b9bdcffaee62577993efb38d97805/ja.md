```
buildFamilyArray(parentVid_vid)
```

ベクトル `vid_child_Vid` を作成します。これは、バリアントIDの `vid` にインデックス付けされており、各バリアントの子供をIDのベクトルとして要素に持ちます。例えば、`vid_child_Vid[5]` は、`vid=5` のバリアントの子供の `vid` の要素を持つベクトル `vid_child` です。

`parentVid_vid`:    バリアントIDの `vid` にインデックス付けされたベクトルで、各要素はそのバリアントの親 `vid` を参照します。例えば、`parentVid_vid[5]` は、`vid=5` のバリアントの親の `vid` です。

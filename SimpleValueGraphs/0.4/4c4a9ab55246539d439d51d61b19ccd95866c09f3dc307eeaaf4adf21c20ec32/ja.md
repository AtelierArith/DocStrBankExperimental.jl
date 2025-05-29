```
set_edgeval!(g::AbstractValGraph, s, d, :, values)
```

エッジ `e: s -> d` の値を `values` に設定します。該当するエッジが存在する場合は `true` を返し、そうでない場合は `false` を返します。

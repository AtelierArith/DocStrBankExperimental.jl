```
objective(workspace; keep_batchdim = false)
```

二重不均衡多マージナル最適輸送目的。`keep_batchdim = true`の場合、`workspace`のバッチサイズが1であってもバッチ次元が保持されます。

理論的には、この値はSinkhornステップの数に応じて単調に増加するはずです。

!!! warn
    この関数は現在、意図した通りに動作していません。


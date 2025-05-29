```
cost(coupling; weighted = true, keep_batchdim = false)
cost(workspace, a, b; weighted = true, keep_batchdim = false)
```

`coupling`に沿ったエッジ`(a, b)`の総輸送コストを計算します。`keep_batchdim = true`の場合、`workspace`のバッチサイズが1であってもバッチ次元が保持されます。`weighted = true`の場合、コスト値はエッジの重みによってスケーリングされます。

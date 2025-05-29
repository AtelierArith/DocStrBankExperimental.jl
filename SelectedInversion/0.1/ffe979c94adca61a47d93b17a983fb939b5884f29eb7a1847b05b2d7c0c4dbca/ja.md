```
get_split_chunk(S::SupernodalMatrix, sup_idx::Int)
```

スーパーノード `sup_idx` に対応するチャンクを取得し、上部に対角線 / 下三角行列ブロックを分割し、その下に残りのブロックを配置します。

```
get_sources(con::SeisCon)
```

ソースの位置座標ペアの配列を返します。最小値と最大値ではありません。`get_headers`とは異なり、`get_sources`は各ブロック全体でSourceXとSourceYが一貫していることを確認します。つまり、`min == max`です。

返される配列の列1はSourceXで、列2はSourceYです。

# 例

sx = get_sources(s)

```
PairwiseFusion(connection, layers...)
```

## 引数

  * `connection`: 2つの入力を受け取り、それらを単一の出力に結合する関数
  * `layers`: 出力が結合されるレイヤー

## 入力

このレイヤーは入力タイプに基づいて異なる動作をします：

1. 入力 `x` が長さ N のタプルである場合（または入力が N 個の `x` を持つ `xs` である場合）、`layers` の数と一致します。

その場合、各レイヤーは新しい入力 `x[i]` を受け取り、前の出力 `y[i-1]` と `connection` を使用して結合します。したがって、`(y1, y2, y3) = PairwiseFusion(connection, layer1, layer2, layer3)((x1, x2, x3))` は次のように描かれます：

```
x1 → layer1 → y1 ↘
                  connection → layer2 → y2 ↘
              x2 ↗                          connection → layer3 → y3
                                        x3 ↗
```

... または次のように書かれます：

```julia
y1 = layer1(x1)
y2 = layer2(connection(y1, x2))
y3 = layer3(connection(y2, x3))
```

2. 入力が1つだけの場合、各レイヤーは同じ `x` を受け取り、前の出力と結合します。したがって、`y = PairwiseFusion(connection, layers...)(x)` は次のように従います：

```julia
y[1] == layers[1](x)
for i in 2:length(layers)
    y[i] == connection(layers[i](y[i-1]), x)
end
```

## 戻り値

各融合の出力を持つ長さ N のタプル（上記の例では (`y1`, `y2`, ..., `yN`)）。

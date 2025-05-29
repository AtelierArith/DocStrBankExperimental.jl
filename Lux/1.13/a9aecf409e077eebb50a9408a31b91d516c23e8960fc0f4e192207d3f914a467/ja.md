```
PairwiseFusion(connection, layers...; name=nothing)
PairwiseFusion(connection; name=nothing, layers...)
PairwiseFusion(; connection, layers..., name=nothing)
```

```
x1 → layer1 → y1 ↘
                  connection → layer2 → y2 ↘
              x2 ↗                          connection → y3
                                        x3 ↗
```

## 引数

  * `connection`: 2つの入力を受け取り、それらを結合します
  * `layers`: `AbstractLuxLayer`s。レイヤーは2つの形式で指定できます：

      * `N`個のLuxレイヤーのリスト
      * `N`個のキーワード引数として指定。

# 拡張ヘルプ

## 入力

レイヤーは入力タイプに基づいて異なる動作をします：

1. 入力 `x` が長さ `N + 1` のタプルである場合、`layers` は長さ `N` のタプルでなければなりません。計算は次のようになります

```julia
y = x[1]
for i in 1:N
    y = connection(x[i + 1], layers[i](y))
end
```

2. その他の種類の入力

```julia
y = x
for i in 1:N
    y = connection(x, layers[i](y))
end
```

## 戻り値

  * 戻り値がどのように計算されるかは入力セクションを参照してください
  * 含まれるすべてのレイヤーの更新されたモデル状態

## パラメータ

  * 各 `layer` のパラメータは、`fields = layer_1, layer_2, ..., layer_N` のNamedTupleでラップされています（kwargs APIを使用する場合、名前は変更されます）

## 状態

  * 各 `layer` の状態は、`fields = layer_1, layer_2, ..., layer_N` のNamedTupleでラップされています（kwargs APIを使用する場合、名前は変更されます）

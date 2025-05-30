TriplewiseFusion(connection, layers...)

```
     u1                    u2
        ↘                     ↘
h1 → layer1 → connection → layer2 → connection
        ↗                     ↗
     v1                    v2
```

## 引数

  * `connection`: 3つの入力を受け取り、それらを組み合わせる関数。
  * `layers`: `AbstractExplicitLayer`または`Chain`。

## 入力

レイヤーは入力タイプに基づいて異なる動作をします：

1. `(h, u, v)`の三つ組で、`u`と`v`はそれ自体が長さ`N`のタプルであり、`layers`も長さ`N`のタプルです。計算は次のようになります。

```julia
for i in 1:N
    h = connection(layers[i](h), u[i], v[i])
end
```

2. `(h, u, v)`の三つ組で、`u`と`v`は`AbstractArray`です。

```julia
for i in 1:N
    h = connection(layers[i](h), u, v)
end
```

## パラメータ

  * 各`layer`のパラメータは、`fields = layer_1, layer_2, ..., layer_N`を持つNamedTupleでラップされています。

## 状態

  * 各`layer`の状態は、`fields = layer_1, layer_2, ..., layer_N`を持つNamedTupleでラップされています。

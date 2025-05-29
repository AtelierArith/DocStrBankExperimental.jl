# コンストラクタ

```
LazyDown(stores_obs)
LazyDown() = LazyDown(x::FelNode -> true)
```

# 説明

下方向のパスを行いたいことを示します。例えば、`sample_down!`。コンストラクタに渡される関数は、`node::FelNode`を入力として受け取り、`node`がその観測値を保存しているかどうかを決定する`Bool`を返します。

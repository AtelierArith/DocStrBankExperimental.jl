```
Model(f, args::NamedTuple[, defaults::NamedTuple = ()])
```

評価関数 `f` と `args` から推測された欠落引数を持つモデルを作成します。

デフォルト引数 `defaults` は、異なる引数を持つ同じモデルのインスタンスを構築する際に内部で使用されます。

```
EvoTree{L,K}
```

`EvoTree`は、適合した勾配ブーストツリーの構造を保持します。

# フィールド

  * trees::Vector{Tree{L,K}}
  * info::Dict

`EvoTree`は、入力データに対して推論を行うためのファンクタとして機能します：

```
pred = (m::EvoTree; ntree_limit=length(m.trees))(x)
```

```
attrs(object::Union{File,Group,Dataset,Datatype})
```

`object`の属性辞書。`object`の属性にアクセスするための`Dict`のようなオブジェクトである`AttributeDict`を返します。

```julia
attrs(object)["name"] = value  # 属性を作成/上書き
attr = attrs(object)["name"]   # 属性を読み取る
delete!(attrs(object), "name") # 属性を削除
keys(attrs(object))            # 属性名のリスト
```

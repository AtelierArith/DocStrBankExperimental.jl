```
nestedget(dict::Dict, keys::AbstractVector, default = nothing)
```

`dict["key1"]["key2"]...["keyn"]` が存在するかどうかを確認し、その値を返すか、`default` を返します。

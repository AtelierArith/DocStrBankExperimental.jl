```
    pdDocClose(doc::PDDoc, num::Int) -> Nothing
```

`PDDoc`オブジェクトに関連付けられたリソースを解放します。一度呼び出されると、`PDDoc`オブジェクトはさらに使用できなくなります。

# 例

```
julia> pdDocClose(doc)
```

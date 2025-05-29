```
    set!(dict::CosDict, name::CosName, obj::CosObject) -> CosDict

    set!(stm::CosStream, name::CosName, obj::CosObject) -> CosStream

```

辞書オブジェクトの値を設定します。`CosNull`オブジェクトを設定すると、辞書からオブジェクトが削除されます。

`CosStream`オブジェクトの場合、データは拡張辞書に追加されます。

# 例

```
julia> set!(catalog, cn"Version", cn"1.4")

julia> <<
...
/Version /1.4
...
>>
```

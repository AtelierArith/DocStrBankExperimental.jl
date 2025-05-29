```
Clamp([; min::Maybe{StorageReal} = nothing, max::Maybe{StorageReal} = nothing])
```

範囲内の値に変換する要素ごとの操作。

**パラメータ**

`min` - 指定された場合、この値より低い値はこの値に増加します。

`max` - 指定された場合、この値より高い値はこの値に増加します。

!!! note
    `min` と `max` のいずれかは必ず指定する必要があります。


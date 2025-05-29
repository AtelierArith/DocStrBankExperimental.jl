```
setlengths!(edges::Vector{Edge}, lengths::AbstractVector)
```

`edges`のベクトルに新しい長さを割り当てます。新しいエッジの長さが非負または`missing`（または-1が`missing`として解釈される）であることを確認します。

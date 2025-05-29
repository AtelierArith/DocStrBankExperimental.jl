```
StdString(str, n::Integer)
```

`str`の最初の`n`コードユニットから`StdString`を作成します（ヌル文字を含む）。

## 例

```julia
julia> StdString("visible\0hidden", 10)
"visible\0hi"
```

```
function averagebymass(data, symbol::Symbol)
function averagebymass(data::StructArray, symbol::Symbol)
```

配列の辞書の配列内の要素の `:Mass` によって重み付けされたフィールド `symbol` の平均

## 例

```jl
averagebymass(data, :Pos)
```

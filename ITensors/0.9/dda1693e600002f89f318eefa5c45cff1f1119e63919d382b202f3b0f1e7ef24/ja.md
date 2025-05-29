```
@disable_warn_order
```

ITensorの順序に関する警告をコードのブロックで無効にします。

# 例

```julia
A = ITensor(IndexSet(_ -> Index(1), Order(8)))
B = ITensor(IndexSet(_ -> Index(1), Order(8)))
A * B
@disable_warn_order A * B
@reset_warn_order A * B
@set_warn_order 17 A * B
@set_warn_order 12 A * B
```

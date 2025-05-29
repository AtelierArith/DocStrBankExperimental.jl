```
@set_warn_order
```

一時的にコードブロック内でITensorの順序に関する警告のしきい値を設定します。

# 例

```julia
@set_warn_order 12 A * B

@set_warn_order 15 begin
  C = A * B
  E = C * D
end
```

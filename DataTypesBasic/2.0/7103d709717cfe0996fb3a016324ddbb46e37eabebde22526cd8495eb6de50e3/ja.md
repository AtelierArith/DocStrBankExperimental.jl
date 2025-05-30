```
either(:left, bool_condition, "right")
```

`bool_condition`が真であれば、右側の値を[Identity](@ref)でラップして返します。そうでなければ、左側を[Const](@ref)でラップして返します。

## 例

```jldoctest
either(:left, 1 < 2, "right") == Identity("right")
```

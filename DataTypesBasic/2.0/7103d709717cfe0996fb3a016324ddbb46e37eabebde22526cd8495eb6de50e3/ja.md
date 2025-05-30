```
either(:left, bool_condition, "right")
```

`bool_condition`が真であれば、右側の値を返し、[Identity](@ref)でラップします。そうでなければ、左側を返し、[Const](@ref)でラップします。

## 例

```jldoctest
either(:left, 1 < 2, "right") == Identity("right")
```

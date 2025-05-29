```
rotation_type(::RotationMethod)
```

与えられた回転方法の回転タイプを返します。

## 例

```jldoctest
julia> rotation_type(Varimax())
直交

julia> rotation_type(Oblimin(gamma = 0.5))
斜交
```

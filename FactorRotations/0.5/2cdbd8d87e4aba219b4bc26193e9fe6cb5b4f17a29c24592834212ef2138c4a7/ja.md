```
isorthogonal(::RotationMethod)
```

提供された回転方法が直交しているかどうかを確認します。

## 例

```jldoctest
julia> isorthogonal(Varimax())
true

julia> isorthogonal(Oblimax(orthogonal = false))
false
```

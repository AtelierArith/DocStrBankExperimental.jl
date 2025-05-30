```
isoblique(::RotationMethod)
```

指定された回転方法が斜めであるかどうかを確認します。

## 例

```jldoctest
julia> isoblique(Varimax())
false

julia> isoblique(Oblimax(orthogonal = false))
true
```

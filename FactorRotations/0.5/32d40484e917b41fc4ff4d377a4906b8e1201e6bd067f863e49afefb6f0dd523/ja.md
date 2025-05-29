```
isoblique(::RotationMethod)
```

指定された回転方法が斜めであるかどうかをチェックします。

## 例

```jldoctest
julia> isoblique(Varimax())
false

julia> isoblique(Oblimax(orthogonal = false))
true
```

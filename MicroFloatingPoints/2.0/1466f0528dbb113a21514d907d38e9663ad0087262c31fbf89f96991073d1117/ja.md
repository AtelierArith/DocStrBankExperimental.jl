```
isinexact(x::Floatmu{szE,szf}) where {szE,szf}
```

値 `x` が `Floatmu{szE,szf}` として作成されたときに丸められた場合は `true` を返し、そうでない場合は `false` を返します。

NaN は決して不正確ではありません。無限大は有限の値から作成された場合のみ不正確です。

# 参照:

  * [`errorsign(x::Floatmu{szE,szf}) where {szE,szf}`](@ref).
  * [`reset_inexact()`](@ref)
  * [`inexact()`](@ref)

# 例

```jldoctest
julia> isinexact(Floatmu{2, 2}(0.25)+Floatmu{2, 2}(2.0))
true
julia> isinexact(Floatmu{2, 2}(0.25)+Floatmu{2, 2}(1.5))
false
```

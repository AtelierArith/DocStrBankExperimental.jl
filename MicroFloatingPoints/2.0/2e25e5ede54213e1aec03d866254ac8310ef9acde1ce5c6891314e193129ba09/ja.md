```
errorsign(x::Floatmu{szE,szf}) where {szE,szf}
```

`Floatmu{szE,szf}`として作成されたときに`x`が過剰に丸められた場合は`1`を返し、デフォルトで丸められた場合は`-1`を返し、丸めが行われなかった場合は`0`を返します。

NaNは決してエラーではありません。無限大は有限の値から作成された場合のみエラーです。

# 参照

  * [`isinexact(x::Floatmu{szE,szf}) where {szE,szf}`](@ref)
  * [`reset_inexact()`](@ref)
  * [`inexact()`](@ref)

# 例

```jldoctest
julia> errorsign(Floatmu{2, 2}(0.5))
0
julia> errorsign(Floatmu{2, 2}(1.7))
1
julia> errorsign(Floatmu{2, 2}(-2.8))
-1
```

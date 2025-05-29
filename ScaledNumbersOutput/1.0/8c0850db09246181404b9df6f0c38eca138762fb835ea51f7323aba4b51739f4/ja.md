```
to_SI(x::Real; sigdigits=5)
```

入力数値 `x` を `sigdigits` 有効桁数で丸められた文字列に変換し、SIスケーリング接頭辞を使用するように変換します。

# 例

```jldoctest julia> to_SI(1.5e9) "1.5G"

julia> to_SI(0.00000025) "250n"

julia> to_SI(1/3) "0.33333"

julia> to_SI(1/3, sigdigits=12) "0.333333333333"
```

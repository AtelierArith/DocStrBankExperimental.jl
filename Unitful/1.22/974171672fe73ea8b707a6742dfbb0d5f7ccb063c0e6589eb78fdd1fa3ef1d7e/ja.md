```
uparse(string [; unit_context=ctx])
```

文字列を単位または量として解析します。`string`の形式は有効なJulia式でなければならず、識別子は`ctx`のコンテキストで検索されます。`ctx`は`Module`または`Module`のベクターである可能性があります。デフォルトでは`unit_context=Unitful`です。

例:

```jldoctest
julia> uparse("m/s")
m s^-1

julia> uparse("1.0*dB")
1.0 dB
```

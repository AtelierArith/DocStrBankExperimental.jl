```
infer_ccn_type(s) -> T<:CCN
```

文字列からCCNの型を推論します。形式は標準的なCCN形式です。

# 引数

  * `s::Union{AbstractString,Integer}` - 標準的なCCN形式の文字列または整数値。

# 戻り値

推論された型で、`CCN`のサブタイプになります。`s`から型を推論できない場合は例外をスローします。

CCN文字列を標準化するには、[`clean_ccn`](@ref)を参照してください。

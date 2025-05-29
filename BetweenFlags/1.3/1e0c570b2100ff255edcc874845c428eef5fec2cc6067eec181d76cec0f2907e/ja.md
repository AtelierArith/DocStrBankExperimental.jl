```
TokenStream(
    code::S,
    flag_set::FlagSet{FP}
) where {S<:AbstractString, FP<:FlagPair}
```

フラグIDをキーとし、フラグのネストの深さを示す`Int`のベクターを値とする辞書。

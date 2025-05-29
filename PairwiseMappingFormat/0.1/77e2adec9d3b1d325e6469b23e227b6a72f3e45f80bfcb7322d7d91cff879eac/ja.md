```
ParserException
```

[`PAFReader`](@ref)を反復処理する際にスローされる例外タイプ、または[`PAFRecord`](@ref)の`parse`が失敗した場合。`try_parse`および`try_next!`関数は、このタイプの値を返すことがあります（スローしません）。エラーが発生した行には、`.line`フィールドでアクセスできます。エラーの種類には、`.kind`フィールドでアクセスできます。

# 例

```jldoctest
julia> err = PAF.try_parse("abc");

julia> err.line
1

julia> print(err.kind)
TooFewFields
```

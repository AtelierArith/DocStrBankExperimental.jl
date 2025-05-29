```
get_stopwords()
```

英語のストップワードを含むDataFrameを返します。

ストップワードは`Languages.jl`パッケージから取得されます: https://github.com/JuliaText/Languages.jl/blob/master/data/stopwords/English.txt。

# 返り値

  * ストップワードを含む単一の列`word`を持つ`DataFrame`。

# 例

```jldoctest
julia> first(get_stopwords(), 5)
5×1 DataFrame
 Row │ word   
     │ String 
─────┼────────
   1 │ a
   2 │ about
   3 │ above
   4 │ across
   5 │ after
```

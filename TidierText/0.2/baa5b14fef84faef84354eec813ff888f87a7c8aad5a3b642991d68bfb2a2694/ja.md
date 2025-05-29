```
nma_words
```

44の英語の否定詞、助動詞、及び副詞を含むDataFrameを返します。

NMAの単語はSaif Mohammadによって開発されたリストから来ています: http://saifmohammad.com/WebPages/SCL.html#NMA

# 返り値

  * `DataFrame`は単一の列`word`を持ち、各行にはストップワードが含まれています。

# 例

```jldoctest
julia> first(nma_words, 5)
5×2 DataFrame
 Row │ word       modifier 
     │ String     String   
─────┼─────────────────────
   1 │ cannot     negator
   2 │ could not  negator
   3 │ did not    negator
   4 │ does not   negator
   5 │ had no     negator
```

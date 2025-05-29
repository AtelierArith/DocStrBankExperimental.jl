TokenSort(dist)

`TokenSort{dist}`距離を作成します。

`TokenSort{dist}`は、単語をアルファベット順に並べ替えた後の文字列間の距離を返します。詳細はhttp://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/を参照してください。

これはAbstractStringsに対してのみ定義されています。

### 例

```julia-repl
julia> s1 = "New York Mets vs Atlanta Braves"
julia> s1 = "New York Mets vs Atlanta Braves"
julia> s2 = "Atlanta Braves vs New York Mets"
julia> TokenSort(RatcliffObershelp())(s1, s2)
0.0
```

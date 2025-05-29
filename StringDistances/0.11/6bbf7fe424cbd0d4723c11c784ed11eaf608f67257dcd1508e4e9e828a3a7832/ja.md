TokenSet(dist)

`TokenSet{dist}`距離を作成します。これはAbstractStringsのみに定義されています。

`TokenSet{dist}`は、次の間の最小距離を返します: [SORTED*INTERSECTION] [SORTED*INTERSECTION] + [SORTED*REST*OF*STRING1] [SORTED*INTERSECTION] + [SORTED*REST*OF_STRING2] 参照: http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/

### 例

```julia-repl
julia> s1 = "New York Mets vs Atlanta"
julia> s2 = "Atlanta Braves vs New York Mets"
julia> TokenSet(RatcliffObershelp())(s1, s2)
0.0
```

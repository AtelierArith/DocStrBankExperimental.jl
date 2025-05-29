Partial(dist)

`Partial{dist}`距離を作成します。

`Partial{dist}`は、短い文字列と、長い文字列の部分文字列との間の最小距離を返します。部分文字列の長さは短い文字列と等しくなります。

http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/ を参照してください。

### 例

```julia-repl
julia> s1 = "New York Mets vs Atlanta Braves"
julia> s2 = "Atlanta Braves vs New York Mets"
julia> Partial(RatcliffObershelp())(s1, s2)
0.5483870967741935
```

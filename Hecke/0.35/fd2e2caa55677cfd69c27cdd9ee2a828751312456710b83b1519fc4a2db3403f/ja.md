```
rational_reconstruction{S}(a::PolyRingElem{S}, b::PolyRingElem{S})
```

`true` と $x/y$ を返します。ここで $ay = x \mod b$ かつ $degree(x), degree(y) <= degree(b)/2$ であるか、そうでなければ `false`（およびガーベッジ）を返します。より一般的な関数へのショートカットです。

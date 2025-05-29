```
pop(s::AbstractSmallSet{N,T}, x, default::U) where {N,T,U} -> Tuple{SmallSet{N,T}, Union{T,U}}
```

`s`が要素`x`を持っている場合、それを削除し、新しいセットと`x`に等しい格納された要素を返します。そうでない場合は、タプル`(SmallSet(d), default)`を返します。

`Base.pop!`も参照してください。

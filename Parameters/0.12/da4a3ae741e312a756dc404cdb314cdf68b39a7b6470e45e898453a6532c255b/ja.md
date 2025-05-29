型インスタンスを辞書に変換します。

```
julia> struct T
           a
           b
       end

julia> type2dict(T(4,5))
Dict{Symbol,Any} with 2 entries:
  :a => 4
  :b => 5
```

これは `getproperty` を使用しています。

```
NoUnits
```

「単位なし」を表すオブジェクト、すなわち単位のない数の単位。オブジェクトの型は `Unitful.FreeUnits{(), NoDims}` です。空の文字列として表示されます。

例:

```jldoctest
julia> unit(1.0) == NoUnits
true
```

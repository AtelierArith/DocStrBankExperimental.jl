```
SortedDict(d, o=Forward)
```

および `SortedDict{K,V}(d, o=Forward)`

通常のJulia辞書 `d`（または任意の連想型）から `SortedDict` を構築します。例えば：

```julia
d = Dict("New York" => 1788, "Illinois" => 1818)
c = SortedDict(d)
```

この例では、キーの型は `String` に推測され、値の型は `Int` になります。

`K` と `V` が指定されていない場合、キーの型と値の型は与えられた辞書から推測されます。順序オブジェクト `o` はデフォルトで `Forward` です。

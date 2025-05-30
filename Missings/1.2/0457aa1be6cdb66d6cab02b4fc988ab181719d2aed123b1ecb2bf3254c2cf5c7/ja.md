```
missingsmallest(f)
```

2つの引数 `x` と `y` を持つ関数を返します。これは `x` が `y` より小さいかどうかをテストしますが、`missing` は常に他の引数より小さいと見なされます。言い換えれば、`missing` が最小の値となるように部分順序関数 `f` の修正バージョンを返します。そして、他のすべての非 `missing` 値は `f` に従って比較されます。

`missing` を最小の値として扱うように修正された標準の `isless` 関数の動作は、2引数の `missingsmallest(x, y)` 関数を呼び出すことで得られます。これは `missingsmallest(isless)(x, y)` と同等です。

# 例

```
julia> isshorter = missingsmallest((s1, s2) -> isless(length(s1), length(s2)));

julia> isshorter("short", "longstring")
true

julia> isshorter("longstring", "short")
false

julia> isshorter("", missing)
false
```

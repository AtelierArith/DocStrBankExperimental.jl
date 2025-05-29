```
ft_round(digits::Union{Int, AbstractVector{Int}}, [columns::AbstractVector{Int}]) -> Function
```

`columns`の要素を`digits`の桁数に丸めます。

`digits`が`Vector`の場合、`columns`も同じ数の要素を持つ`Vector`でなければなりません。`digits`が`Number`で、`columns`が指定されていない（または空である）場合、丸めはテーブル全体に適用されます。それ以外の場合、`digits`が`Number`で`columns`が`Vector`の場合、`columns`の列の要素は`digits`の桁数に丸められます。

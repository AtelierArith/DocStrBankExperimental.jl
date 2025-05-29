```
ft_printf(ftv_str::Union{String, Vector{String}}, [columns::AbstractVector{Int}]) -> Function
```

`ftv_str`（`Printf`標準ライブラリを参照）を使用して、`columns`の要素にフォーマットを適用します。

`ftv_str`が`Vector`の場合、`columns`も同じ数の要素を持つ`Vector`でなければなりません。`ftv_str`が`String`で、`columns`が指定されていない（または空）場合、フォーマットはテーブル全体に適用されます。そうでない場合、`ftv_str`が`String`で、`columns`が`Vector`の場合、フォーマットは`columns`内の列にのみ適用されます。

!!! info
    このフォーマッタは、`Number`型のセルにのみ適用されます。


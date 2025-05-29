```
@foreach_chain_candidate chain_var i_start i_end chain_length inner_expr
```

長さ `chain_length` のすべての昇順のタプル `(i_start, ..., i_end)` を反復処理します。このタプルは、内部式ブロック内で `chain_var` と名付けられます。

# 例

```jldoctest
@foreach_chain_candidate I 1 5 4 begin
    @show I
end

# 出力

I = (1, 1, 1, 5)
I = (1, 1, 2, 5)
I = (1, 1, 3, 5)
I = (1, 1, 4, 5)
I = (1, 1, 5, 5)
I = (1, 2, 2, 5)
I = (1, 2, 3, 5)
I = (1, 2, 4, 5)
I = (1, 2, 5, 5)
I = (1, 3, 3, 5)
I = (1, 3, 4, 5)
I = (1, 3, 5, 5)
I = (1, 4, 4, 5)
I = (1, 4, 5, 5)
I = (1, 5, 5, 5)
```

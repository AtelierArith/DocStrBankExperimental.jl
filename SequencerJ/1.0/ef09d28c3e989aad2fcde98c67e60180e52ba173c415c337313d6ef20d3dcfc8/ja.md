ベクトルの最初と最後の `len` 要素を文字列として返します。

デフォルトでは、先頭と末尾に3つの要素を表示します。

```julia
julia> v = collect(1:10);
julia> prettyp(v)

"1,2,3...8,9,10"
```

5つの要素が表示される例

```julia
julia> v = collect(1:10);
julia> prettyp(v, 5)

"1,2,3,4,5...6,7,8,9,10"
```

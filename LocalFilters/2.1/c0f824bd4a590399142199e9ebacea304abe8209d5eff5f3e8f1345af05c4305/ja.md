```
B = reverse_kernel(args...)
```

は、`B[i] == A[-i]` が成り立つように、`A = kernel(args...)` に似たカーネル `B` を生成します。ただし、`i` が `A` の有効なインデックスである限り、`B` は逆順になります。その結果、`B` による相関は `A` による畳み込みと同じ結果をもたらし、逆もまた然りです。

[`LocalFilters.kernel`](@ref) および [`LocalFilters.strel`](@ref) も参照してください。

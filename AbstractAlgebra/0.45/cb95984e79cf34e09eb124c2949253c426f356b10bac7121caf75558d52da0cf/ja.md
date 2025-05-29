```
Base.getindex(M::MatElem, rows, cols)
```

`rows` と `cols` が `AbstractVector{Int}` として指定されると、$A$ のコピーを返します。$A$ は `A[i,j] = M[rows[i], cols[j]]` によって定義され、$i=1,...,length(rows)$ および $j=1,...,length(cols)$ の範囲で計算されます。ベクトルの代わりに、`rows` と `cols` は次のようにも指定できます：

  * 整数 `i` は `i:i` と解釈され、
  * `:` はそれぞれ `1:nrows(M)` または `1:ncols(M)` と解釈されます。

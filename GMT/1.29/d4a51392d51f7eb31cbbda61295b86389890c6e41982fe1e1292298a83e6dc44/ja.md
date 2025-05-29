```
u, ind = gunique(x::AbstractVector; sorted=false)
```

配列 `x` のユニークな要素のみを含む配列を返し、`u = x[ind]` となるインデックス `ind` を返します。`sorted` が true の場合、出力はソートされます（デフォルトはソートされていません）。

```
u, ic, ia = gunique(x::AbstractMatrix; sorted::Bool=false, rows=true)
```

Matlab の unique(x, 'rows') のように動作し、ここで `u = x(ia,:)` および `x = u(ic,:)` となります。`rows` が false の場合、`ic` は空になります。

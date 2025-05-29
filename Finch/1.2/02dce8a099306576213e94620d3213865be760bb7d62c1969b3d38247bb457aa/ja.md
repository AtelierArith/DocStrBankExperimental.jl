```
minby(a, b)
```

`a` または `b` の最小値を返し、`a[1]` と `b[1]` を比較し、左側での引き分けを解消します。argmin 操作を実装するのに便利です：

```jldoctest setup=:(using Finch)
julia> a = [7.7, 3.3, 9.9, 3.3, 9.9]; x = Scalar(Inf => 0);

julia> @finch for i=_; x[] <<minby>>= a[i] => i end;

julia> x[]
3.3 => 2
```

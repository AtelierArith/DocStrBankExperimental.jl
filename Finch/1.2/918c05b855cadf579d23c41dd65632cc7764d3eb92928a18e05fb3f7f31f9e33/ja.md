```
maxby(a, b)
```

`a` または `b` の最大値を返し、`a[1]` と `b[1]` を比較し、同点の場合は左側を優先します。argmax 操作を実装するのに便利です：

```jldoctest setup=:(using Finch)
julia> a = [7.7, 3.3, 9.9, 3.3, 9.9]; x = Scalar(-Inf => 0);

julia> @finch for i=_; x[] <<maxby>>= a[i] => i end;

julia> x[]
9.9 => 3
```

```
choose(z)(a, b)
```

`choose(z)` は、`a` または `b` のうち、`z` と等しくない方を返す関数です。どちらも `z` でない場合は、`a` を返します。スパース配列で最初の非フィル値を取得するのに便利です。

```jldoctest setup=:(using Finch)
julia> a = Tensor(SparseList(Element(0.0)), [0, 1.1, 0, 4.4, 0])
5 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, ElementLevel{0.0, Float64, Int64, Vector{Float64}}}}:
 0.0
 1.1
 0.0
 4.4
 0.0

julia> x = Scalar(0.0); @finch for i=_; x[] <<choose(0.0)>>= a[i] end;

julia> x[]
1.1
```

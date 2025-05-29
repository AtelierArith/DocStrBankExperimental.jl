```
TV_cuda(; num_dims=2)
```

この関数は、2次元または3次元配列のトータルバリエーション正則化子を計算する関数を返します。 `num_dims` は `2` または `3` のいずれかにすることができます。

```julia-repl
julia> using CUDA

julia> reg = TV_cuda(num_dims=2);

julia> reg(CuArray([1 2 3; 4 5 6; 7 8 9]))
12.649111f0
```

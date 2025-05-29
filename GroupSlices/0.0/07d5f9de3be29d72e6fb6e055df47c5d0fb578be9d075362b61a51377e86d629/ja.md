```
groupslices(A; dims) = groupslices(A, dims)
```

整数のベクトルを返します。返されるベクトルの各整数要素は、`unique(A; dims=d)`から返される次元`dims`に沿ったユニークなスライスに対応するグループ番号です。`A`は多次元配列であることができます。デフォルトは`dims = 1`です。

使用例:

もし`C = unique(A; dims=dims)`、`ic = groupslices(A, dims)`、および`ndims(A) == ndims(C) == 3`であれば、次のようになります:

```
if dims == 1
   all(A .== C[ic,:,:])
elseif dims == 2
   all(A .== C[:,ic,:])
elseif dims == 3
   all(A .== C[:,:,ic])
end
```

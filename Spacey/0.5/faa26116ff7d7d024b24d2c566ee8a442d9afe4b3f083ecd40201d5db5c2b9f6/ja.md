格子の対称操作を生成します。これは三つの3次元ベクトルによって定義されます。この関数は`pointGroup_basic`よりも効率的であることを目的としているため、より複雑です。

```juliadoctest
julia> u = [1,0,0]; v = [.5,√3/2,0]; w = [0,0,√(8/3)];
julia> pointGroup(u,v,w)
24-element Array{Array{Float64,2},1}:
[-1 -1 0; 0 1 0; 0 0 -1]
...
```

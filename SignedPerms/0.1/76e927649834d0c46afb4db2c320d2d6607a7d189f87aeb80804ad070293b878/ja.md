`SPerm(M::AbstractMatrix,N::AbstractMatrix;dims)`

は、`invpermute(N,p;dims)==M` となるような符号付き置換 `p` を返します。もしそのような `p` が存在しない場合は `nothing` を返します。`dims=(1,2)` の場合、`M` と `N` は対称行列である必要があります。

`dims=(1,2)` の場合のルーチンは、異なるラベリングを持つが同型の2つのオブジェクトを特定するのに役立ちます。これは、標準（分類された）データを持つルスティグ・フーリエ変換行列を特定するために Chevie で使用されます。このプログラムは高度なアルゴリズムを使用しており、最大80×80の行列を扱うことができます。

```julia-repl
julia> p=sperm"(1,-1)(2,5,3,-4,-2,-5,-3,4)(7,-9)";

julia> m=onmats(n,p);

julia> onmats(n,SPerm(m,n;dims=(1,2)))==m
true
```

与えられたノットベクトル $k$ に対して、次の関数 $\mathfrak{n}_k:\mathbb{R}\to\mathbb{Z}$ は、ノットベクトル $k$ を重複させるノットの数を表します。

$$
\mathfrak{n}_k(t) = \#\{i \mid k_i=t \}
$$

例えば、$k=(1,2,2,3)$ の場合、$\mathfrak{n}_k(0.3)=0$、$\mathfrak{n}_k(1)=1$、$\mathfrak{n}_k(2)=2$ です。

```jldoctest
julia> k = KnotVector([1,2,2,3]);


julia> countknots(k,0.3)
0

julia> countknots(k,1.0)
1

julia> countknots(k,2.0)
2
```

For given knot vector $k$, the following function $\mathfrak{n}_k:\mathbb{R}\to\mathbb{Z}$ represents the number of knots that duplicate the knot vector $k$.

$$
\mathfrak{n}_k(t) = \#\{i \mid k_i=t \}
$$

For example, if $k=(1,2,2,3)$, then $\mathfrak{n}_k(0.3)=0$, $\mathfrak{n}_k(1)=1$, $\mathfrak{n}_k(2)=2$.

```jldoctest
julia> k = KnotVector([1,2,2,3]);


julia> countknots(k,0.3)
0

julia> countknots(k,1.0)
1

julia> countknots(k,2.0)
2
```

```
fdiff_weight(k::Int, j::Int)
```

有限差分重み係数、

$$
c_{j}^{k}=(-1)^{j}\binom{k}{j}.
$$

#### 例:

```
julia> c(k,j) = fdiff_weight(k,j);

julia> a = [[c(k,j) for j=0:k] for k=0:3]
4-element Vector{Vector{Int64}}:
 [1]
 [1, -1]
 [1, -2, 1]
 [1, -3, 3, -1]

julia> b = [[c(k,k-j) for j=0:k] for k=0:3]
4-element Vector{Vector{Int64}}:
 [1]
 [-1, 1]
 [1, -2, 1]
 [-1, 3, -3, 1]

julia> b == reverse.(a)
true
```

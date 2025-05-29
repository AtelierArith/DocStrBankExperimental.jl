```
McCullagh_test(mat::Matrix{Int})
```

Peform the McCullagh's test on a square contigency table `mat`.

McCullagh's test for a kxk contigency table;

see Biometrika, 1977, 64(3), 449-453.

Test case (Table 1 in p. 452) 

Example

```jldoctest
julia> mat = [43 8 3 0; 2 2 5 3; 1 0 7 2; 0 0 1 5]
julia> McCullagh_test(mat)
(0.005469174895116946, 1.4504988072997458, 1.502600073417028, 0.5221345956920705, 2.778017046308073)
```

Expected N matrix

```jldoctest
3×3 Matrix{Int64}:
 14   4  0
  4  12  3
  0   3  6
```

Expected R vector

```jldoctest
[11 11 5]'
```

Expected Δ1 = 1.45, Δ2 = 1.50, std. error = 0.53

```
(X,Y) = sylvsys(A,B,C,D,E,F)
```

シルベスター行列方程式系を解きます

```
            AX + YB = C
            DX + YE = F,
```

ここで、`(A,D)`、`(B,E)`は同じサイズの正方行列のペアです。ペンシル `A-λD` と `-B+λE` は正則であり、共通の固有値を持ってはいけません。

# 例

```jldoctest
julia> A = [3. 4.; 5. 6.]
2×2 Array{Float64,2}:
 3.0  4.0
 5.0  6.0

julia> B = [1. 1.; 1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> C = [-1. -2.; 2. -1.]
2×2 Array{Float64,2}:
 -1.0  -2.0
  2.0  -1.0

julia> D = [1. -2.; -2. -1.]
2×2 Array{Float64,2}:
  1.0  -2.0
 -2.0  -1.0

julia> E = [1. -1.; -2. 2.]
2×2 Array{Float64,2}:
  1.0  -1.0
 -2.0   2.0

julia> F = [1. -1.; -2. 2.]
2×2 Array{Float64,2}:
  1.0  -1.0
 -2.0   2.0

julia> X, Y = sylvsys(A, B, C, D, E, F);

julia> X
2×2 Array{Float64,2}:
  1.388  -1.388
 -0.892   0.892

julia> Y
2×2 Array{Float64,2}:
 -1.788  0.192
  0.236  0.176

julia> A*X + Y*B - C
2×2 Array{Float64,2}:
  6.66134e-16  2.22045e-15
 -3.10862e-15  2.66454e-15

julia> D*X + Y*E - F
2×2 Array{Float64,2}:
  1.33227e-15  -2.22045e-15
 -4.44089e-16   4.44089e-16
```

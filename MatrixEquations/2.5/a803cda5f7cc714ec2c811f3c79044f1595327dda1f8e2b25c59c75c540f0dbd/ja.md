```
X = lyapc(A, E, C)
```

一般化連続リャプノフ方程式の解 `X` を計算します。

```
 AXE' + EXA' + C = 0,
```

ここで `A` と `E` は正方形の実数または複素行列であり、`C` は正方行列です。ペンシル `A-λE` は、`α` と `β` の2つの固有値が `α+β = 0` であってはなりません。解 `X` は、`C` が対称またはエルミートであれば対称またはエルミートです。

以下の特定のケースも扱います。

```
X = lyapc(A,β*I,C)  または  X = lyapc(A,β,C)
```

行列方程式 `AXβ' + βXA' + C = 0` を解きます。

```
X = lyapc(α*I,E,C)  または  X = lyapc(α,E,C)
```

行列方程式 `αXE' + EXα' + C = 0` を解きます。

```
X = lyapc(α*I,β*I,C)  または  X = lyapc(α,β,C)
```

行列方程式 `(αβ'+α'β)X + C = 0` を解きます。

```
x = lyapc(α,β,γ)
```

方程式 `(αβ'+α'β)x + γ = 0` を解きます。

# 例

```jldoctest
julia> A = [3. 4.; 5. 6.]
2×2 Array{Float64,2}:
 3.0  4.0
 5.0  6.0

julia> E = [ 1. 2.; 0. 1.]
2×2 Array{Float64,2}:
 1.0  2.0
 0.0  1.0

julia> C = [1. 1.; 1. 2.]
2×2 Array{Float64,2}:
 1.0  1.0
 1.0  2.0

julia> X = lyapc(A, E, C)
2×2 Array{Float64,2}:
 -2.5   2.5
  2.5  -2.25

julia> A*X*E' + E*X*A' + C
2×2 Array{Float64,2}:
 -5.32907e-15  -2.66454e-15
 -4.44089e-15   0.0
```

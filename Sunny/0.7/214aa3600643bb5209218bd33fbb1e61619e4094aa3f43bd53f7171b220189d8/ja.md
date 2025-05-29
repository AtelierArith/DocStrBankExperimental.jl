```
function print_stevens_expansion(op)
```

ローカルエルミート演算子をスティーブンス演算子の線形結合として表示します。演算子 `op` は有限次元行列または大きな $s$ 限界における抽象スピン多項式である可能性があります。

# 例

```julia
S = spin_matrices(2)
print_stevens_expansion(S[1]^4 + S[2]^4 + S[3]^4)
# Prints: (1/20)𝒪₄₀ + (1/4)𝒪₄₄ + 102/5

S = spin_matrices(Inf)
print_stevens_expansion(S[1]^4 + S[2]^4 + S[3]^4)
# Prints: (1/20)𝒪₄₀ + (1/4)𝒪₄₄ + (3/5)𝒮⁴
```

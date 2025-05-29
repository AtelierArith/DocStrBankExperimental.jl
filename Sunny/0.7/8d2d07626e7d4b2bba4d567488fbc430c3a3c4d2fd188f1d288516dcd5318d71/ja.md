```
spin_matrices(s)
```

$$
N×N
$$

スピン行列の三重項を返します。ここで、$N = 2s+1$ です。これらはスピン `s` 表現における SU(2) の生成子です。

`s == Inf` の場合、返される値は可換な無限次元行列を示す抽象記号です。これらは歴史的研究を繰り返したり、マイクロ磁気システムをモデル化するのに役立ちます。技術的な議論は Sunny ドキュメントページの [Interaction Renormalization](@ref) に記載されています。

# 例

```julia
S = spin_matrices(3/2)
@assert S'*S ≈ (3/2)*(3/2+1)*I
@assert S[1]*S[2] - S[2]*S[1] ≈ im*S[3]

S = spin_matrices(Inf)
@assert S[1]*S[2] - S[2]*S[1] == 0
```

他にも [`print_stevens_expansion`](@ref) を参照してください。

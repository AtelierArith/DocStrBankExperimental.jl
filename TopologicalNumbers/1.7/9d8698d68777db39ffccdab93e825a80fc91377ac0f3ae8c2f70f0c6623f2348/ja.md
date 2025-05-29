Haldaneモデルのハミルトニアン。

```
 Haldane(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Union{AbstractVector,Tuple}}
```

# 引数

  * `k::T1`: 二次元波数 `k`。
  * `p::T2`: 以下に定義されたパラメータ。

# 定義

Haldaneモデルのハミルトニアンは次のように定義されます。

$$
H(\bm{k})=\begin{pmatrix}
    h_{0}(\bm{k})+h_{3}(\bm{k})  & h_{1}(\bm{k})-ih_{2}(\bm{k}) \\
    h_{1}(\bm{k})+ih_{2}(\bm{k}) & h_{0}(\bm{k})-h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{0}(\bm{k})=&2t_{2}\cos(\phi)(\sin(k_{1})+\sin(k_{2})+\sin(k_{1}+k_{2})) \\
     h_{1}(\bm{k})=&-t_{1}(1+\cos(k_{1})+\cos(k_{2})) \\
     h_{2}(\bm{k})=&-t_{1}(-\sin(k_{1})+\sin(k_{2})) \\
     h_{3}(\bm{k})=&m+2t_{2}\sin(\phi)(\sin(k_{1})+\sin(k_{2})-\sin(k_{1}+k_{2}))
\end{align*}
$$

ここで、$t_{1}$と$t_{2}$はタイトバインディングモデルにおける最近接および次最近接隣接ホッピングの振幅です。$\phi$は静的磁場の適用によって生じる位相です。$t_{1}=1$、$t_{2},\phi,m=$`p`で無次元化します。

# 例

```julia
julia> Haldane([0, π/3], [0.5, π/2, 0.3])
2×2 Matrix{ComplexF64}:
  0.3-0.0im       -2.5+0.866025im
 -2.5-0.866025im  -0.3-0.0im
```

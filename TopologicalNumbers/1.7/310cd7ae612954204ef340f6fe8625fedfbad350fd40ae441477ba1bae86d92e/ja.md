Kane–Meleモデルのハミルトニアン。

```
 KaneMele(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Real}
```

# 引数

  * `k::T1`: 二次元波数 `k`。
  * `p::T2`: 以下に定義されるパラメータ。

# 定義

Kane–Meleモデルのハミルトニアンは次のように定義されます。

$$
H(k)=\begin{pmatrix}
    h_{3}(\bm{k})                & 0                            & h_{5}(\bm{k})-ih_{4}(\bm{k}) & 0                            \\
    0                            & -h_{3}(\bm{k})               & 0                            & h_{5}(\bm{k})-ih_{4}(\bm{k}) \\
    h_{5}(\bm{k})+ih_{4}(\bm{k}) & 0                            & -h_{3}(\bm{k})               & 0                            \\
    0                            & h_{5}(\bm{k})+ih_{4}(\bm{k}) & 0                            & h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{3}(\bm{k})=&2\lambda_{\mathrm{SO}}(\sin(k_{1})-\sin(k_{2})-\sin(k_{1}-k_{2})) \\
     h_{4}(\bm{k})=&-t(\sin(k_{1})+\sin(k_{2})) \\
     h_{5}(\bm{k})=&-t(\cos(k_{1})+\cos(k_{2})+1)
\end{align*}
$$

ここで、$t$はタイトバインディングモデルにおける最近接隣接ホッピングの振幅です。$\lambda_{\mathrm{SO}}$はスピン軌道相互作用の大きさです。$t=1$および$\lambda_{\mathrm{SO}}=$`p`で無次元化します。

# 例

```julia
julia> KaneMele([0, π/3], 0.5)
4×4 Matrix{ComplexF64}:
  0.0+0.0im        0.0+0.0im       -2.5+0.866025im   0.0+0.0im
  0.0+0.0im        0.0+0.0im        0.0+0.0im       -2.5+0.866025im
 -2.5-0.866025im   0.0+0.0im        0.0+0.0im        0.0+0.0im
  0.0+0.0im       -2.5-0.866025im   0.0+0.0im        0.0+0.0im
```

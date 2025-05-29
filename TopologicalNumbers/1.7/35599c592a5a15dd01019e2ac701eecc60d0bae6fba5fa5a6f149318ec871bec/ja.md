格子ディラックモデルのハミルトニアン。

```
 LatticeDirac(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple},T2<:Real}
```

# 引数

  * `k::T1`: 四次元波数 `k`。
  * `p::T2`: 以下で定義されるパラメータ。

# 定義

格子ディラックモデルのハミルトニアンは次のように定義されます。

$$
H(k)=\begin{pmatrix}
    h_{4}(\bm{k})                & h_{2}(\bm{k})-ih_{3}(\bm{k}) & h_{0}(\bm{k})-ih_{1}(\bm{k})  & 0                             \\
    h_{2}(\bm{k})+ih_{3}(\bm{k}) & -h_{4}(\bm{k})               & 0                             & h_{0}(\bm{k})-ih_{1}(\bm{k})  \\
    h_{0}(\bm{k})+ih_{1}(\bm{k}) & 0                            & -h_{4}(\bm{k})                & -h_{2}(\bm{k})+ih_{3}(\bm{k}) \\
    0                            & h_{0}(\bm{k})+ih_{1}(\bm{k}) & -h_{2}(\bm{k})-ih_{3}(\bm{k}) & h_{4}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{0}(\bm{k})=&m+c(cos(k_{1})+cos(k_{2})+cos(k_{3})+cos(k_{4})) \\
     h_{1}(\bm{k})=&sin(k_{1}) \\
     h_{2}(\bm{k})=&sin(k_{2}) \\
     h_{3}(\bm{k})=&sin(k_{3}) \\
     h_{4}(\bm{k})=&sin(k_{4})
\end{align*}
$$

ここで、、、

# 例

```julia julia> LatticeDirac([0, 0, 0, π/2], 0.5) 4×4 Matrix{ComplexF64}:  1.0+0.0im   0.0+0.0im   3.5+0.0im  0.0+0.0im  0.0+0.0im  -1.0+0.0im   0.0+0.0im  3.5+0.0im  3.5+0.0im   0.0+0.0im  -1.0+0.0im  0.0+0.0im  0.0+0.0im   3.5+0.0im   0.0+0.0im  1.0+0.0im

```

ハミルトニアンのサウレスポンピングモデル。

```
 ThoulessPump(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Union{AbstractVector,Tuple}}
```

# 引数

  * `k::T1`: 一次元波数 `k₁` と時間 `t` のとき、`k=[k₁, t]`。
  * `p::T2`: 以下に定義されたパラメータ。

# 定義

ケイン–メレモデルのハミルトニアンは次のように定義されます。

$$
H(k)=\begin{pmatrix}
    h_{3}(\bm{k})                 & h_{5}(\bm{k})-ih_{4}(\bm{k}) & 0                            & -h_{5}(\bm{k})-ih_{1}(\bm{k}) \\
    h_{5}(\bm{k})+ih_{4}(\bm{k})  & -h_{3}(\bm{k})               & h_{5}(\bm{k})-ih_{1}(\bm{k}) & 0                             \\
    0                             & h_{5}(\bm{k})+ih_{1}(\bm{k}) & -h_{3}(\bm{k})               & h_{5}(\bm{k})-ih_{4}(\bm{k})  \\
    -h_{5}(\bm{k})+ih_{1}(\bm{k}) & 0                            & h_{5}(\bm{k})+ih_{4}(\bm{k}) & h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{1}(\bm{k})=&-\Delta\sin(k_{1}) \\
     h_{2}(\bm{k})=&-\Delta(1-\cos(k_{1})) \\
     h_{3}(\bm{k})=&m_{0}\sin(t) \\
     h_{4}(\bm{k})=&-t_{0}(1+\cos(t))\sin(k_{1}) \\
     h_{5}(\bm{k})=&-t_{0}(1-\cos(t))-t_{0}(1+\cos(t)))\cos(k_{1})
\end{align*}
$$

ここで、$t_{0}$ はタイトバインディングモデルにおける最近接隣接ホッピングの振幅です。$m_{0}$ は交互の磁場の大きさです。$\Delta$ はスピン反転相互作用の大きさです。$t_{0}=1$ として無次元化し、$m_{0},\Delta=$`p`。

# 例

```julia
julia> ThoulessPump([0, π/3], (-1.0, 0.5))
4×4 Matrix{ComplexF64}:
 -0.866025-0.0im      -2.0+0.0im      -0.0-0.0im        0.0+0.0im
      -2.0-0.0im  0.866025-0.0im      -0.0+0.0im       -0.0-0.0im
      -0.0-0.0im      -0.0-0.0im  0.866025-0.0im       -2.0+0.0im
       0.0-0.0im      -0.0-0.0im      -2.0-0.0im  -0.866025-0.0im
```

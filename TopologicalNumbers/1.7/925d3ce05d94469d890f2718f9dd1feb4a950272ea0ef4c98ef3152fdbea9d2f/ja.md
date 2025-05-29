Bernevig–Hughes–Zhang (BHZ)モデルのハミルトニアン。

```
 BHZ(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Union{AbstractVector,Tuple}}
```

# 引数

  * `k::T1`: 二次元波数 `k`。
  * `p::T2`: 以下に定義されたパラメータ。

# 定義

BHZモデルのハミルトニアンは次のように定義されます。

$$
H(k)=\begin{pmatrix}
    h_{0}(\bm{k})+h_{3}(\bm{k})  & 0                            & h_{5}(\bm{k})-ih_{4}(\bm{k}) & 0                            \\
    0                            & h_{0}(\bm{k})-h_{3}(\bm{k})  & 0                            & h_{5}(\bm{k})-ih_{4}(\bm{k}) \\
    h_{5}(\bm{k})+ih_{4}(\bm{k}) & 0                            & h_{0}(\bm{k})-h_{3}(\bm{k})  & 0                            \\
    0                            & h_{5}(\bm{k})+ih_{4}(\bm{k}) & 0                            & h_{0}(\bm{k})+h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{0}(\bm{k})=&-(t_{ss}-t_{pp})(\cos(k_{1})+\cos(k_{2}))+\frac{(\epsilon_{s}+\epsilon_{p})}{2} \\
     h_{3}(\bm{k})=&2t_{sp}\sin(k_{2}) \\
     h_{4}(\bm{k})=&2t_{sp}\sin(k_{1}) \\
     h_{5}(\bm{k})=&-(t_{ss}+t_{pp})(\cos(k_{1})+\cos(k_{2}))+\frac{(\epsilon_{s}-\epsilon_{p})}{2}
\end{align*}
$$

ここで、$t_{sp}$はタイトバインディングモデルにおけるs軌道とp軌道の間の混合ホッピングの振幅です。$t_{ss}$はs軌道間のホッピング、$t_{pp}$はp軌道間のホッピングであり、$t_{1}=t_{s}-t_{p}$、$t_{2}=t_{s}+t_{p}$です。$\epsilon_{s}$と$\epsilon_{p}$はs軌道とp軌道のサイトポテンシャル項であり、$\epsilon_{1}=\epsilon_{s}+\epsilon_{p}$、$\epsilon_{2}=\epsilon_{s}-\epsilon_{p}$です。$t_{sp}=t_{1}=\epsilon_{1}=1$、$\epsilon_{2},t_{2}=$`p`で無次元化します。

# 例

```julia
julia> BHZ([0, π/3], [0.5, 0.5])
4×4 Matrix{ComplexF64}:
 0.732051+0.0im       0.0+0.0im      -0.5+0.0im       0.0+0.0im
      0.0+0.0im  -2.73205+0.0im       0.0+0.0im      -0.5+0.0im
     -0.5+0.0im       0.0+0.0im  -2.73205+0.0im       0.0+0.0im
      0.0+0.0im      -0.5+0.0im       0.0+0.0im  0.732051+0.0im
```

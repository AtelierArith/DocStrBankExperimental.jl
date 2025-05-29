Kitaevハニカムモデルのハミルトニアン。

```
 KitaevHoneycomb(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Real}
```

# 引数

  * `k::T1`: 二次元波数 `k`。
  * `p::T2`: 以下で定義されるパラメータ。

# 定義

Kitaevハニカムモデルのハミルトニアンは次のように定義されます。

$$
H(\bm{k})=\begin{pmatrix}
    h_{3}(\bm{k})                & h_{1}(\bm{k})-ih_{2}(\bm{k}) \\
    h_{1}(\bm{k})+ih_{2}(\bm{k}) & -h_{3}(\bm{k})
\end{pmatrix}
$$

$$
\begin{align*}
     h_{1}(\bm{k})=&-K_{2}(\sin(k_{2})-\sin(k_{1})+\sin(k_{1}-k_{2})) \\
     h_{2}(\bm{k})=&-K_{1}(\sin(k_{1})+\sin(k_{2})) \\
     h_{3}(\bm{k})=&K_{1}(\cos(k_{1})+\cos(k_{2})+1)
\end{align*}
$$

ここで、$K_{1}$はKitaev相互作用の大きさです。$K_{2}$は磁場によるスピントリプル項の大きさです。$K_{1}=1$および$K_{2}=$`p`で無次元化します。

# 例

```julia
julia> KitaevHoneycomb([0, π/3], 0.5)
2×2 Matrix{ComplexF64}:
 2.5-0.0im        0.0+0.866025im
 0.0-0.866025im  -2.5-0.0im
```

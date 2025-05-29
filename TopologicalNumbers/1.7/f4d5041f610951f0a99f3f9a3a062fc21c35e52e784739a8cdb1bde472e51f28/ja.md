二次元正方格子のフラックスモデルのハミルトニアン。

```
 Flux2d(k::T1, p::T2) where {T1<:Union{AbstractVector,Tuple}, T2<:Union{AbstractVector,Tuple}}
```

# 引数

  * `k::T1`: 一次元波数 `k`。
  * `p::T2`: 以下に定義されたパラメータ。

# 定義

二次元正方格子のフラックスモデルのハミルトニアンは次のように定義されます。

$$
H(k)=\begin{pmatrix}
    -2t\cos(k_{2}-2\pi m\frac{1}{n}) & -t                               & 0      & 0  & \cdots                               & e^{-ik_{1}}           \\
    -t                               & -2t\cos(k_{2}-2\pi m\frac{2}{n}) & -t     & 0  & \cdots                               & 0                     \\
    0                                & -t                               & \ddots & -t & \cdots                               & \vdots                \\
    \vdots                           & \vdots                           &        & -t & -2t\cos(k_{2}-2\pi m\frac{(n-1)}{n}) & -t                    \\
    e^{ik_{1}}                       & 0                                & \cdots & 0  & -t                                   & -2t\cos(k_{2}-2\pi m)
\end{pmatrix}
$$

ここで、$t$はタイトバインディングモデルにおける最近接隣接ホッピングの振幅です。$n$と$m$は静的磁場の適用によって生成される位相の単位セルのサイズです。$t=1$、$n,m=$`p`で無次元化します。

# 例

```julia
julia> Flux2d([0, π/3], [4, 1])
4×4 Matrix{ComplexF64}:
 -1.73205+0.0im  -1.0+0.0im      0.0+0.0im  -1.0+0.0im
     -1.0+0.0im   1.0+0.0im     -1.0+0.0im   0.0+0.0im
      0.0+0.0im  -1.0+0.0im  1.73205+0.0im  -1.0+0.0im
     -1.0-0.0im   0.0+0.0im     -1.0+0.0im  -1.0+0.0im
```

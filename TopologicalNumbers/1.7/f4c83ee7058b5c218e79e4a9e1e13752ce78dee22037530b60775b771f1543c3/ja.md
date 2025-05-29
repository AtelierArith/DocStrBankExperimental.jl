Kitaevチェーンモデルのハミルトニアン。

```
 KitaevChain(k::T1, p::T2) where {T1<:Real, T2<:Union{AbstractVector,Tuple}}
```

# 引数

  * `k::T1`: 一次元波数 `k`。
  * `p::T2`: 以下に定義されたパラメータ。

# 定義

Kitaevチェーンモデルのハミルトニアンは次のように定義されます。

$$
H(k)=\begin{pmatrix}
    -\mu-2t\cos(k)   & 2i\Delta\sin(k) \\
    -2i\Delta\sin(k) & \mu+2t\cos(k)
\end{pmatrix}
$$

ここで、$t$はタイトバインディングモデルにおける最近接隣接ホッピングの振幅です。$\Delta$は最近接隣接サイトとのペアリング、$\mu$は化学ポテンシャルです。$t=1$、$\mu,\Delta=$`p`で無次元化します。

# 例

```julia
julia> SSH(π/3, 0.5)
2×2 Matrix{ComplexF64}:
 -0.5+0.0im       0.0+0.866025im
  0.0-0.866025im  0.5+0.0im
```

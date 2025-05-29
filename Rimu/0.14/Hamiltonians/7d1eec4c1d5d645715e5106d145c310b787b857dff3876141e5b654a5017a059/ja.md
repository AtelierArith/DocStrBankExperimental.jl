```
GutzwillerSampling(::AbstractHamiltonian; g)
```

Gutzwillerサンプリングを実装する任意の[`AbstractHamiltonian`](@ref)のラッパーです。この重要度サンプリング方式では、ハミルトニアンが次のように修正されます。

$$
\tilde{H}_{ij} = H_{ij} e^{-g(H_{ii} - H_{jj})} .
$$

このようにして、オフダイアゴナルの高エネルギー構成へのスパウンは抑制され、正の`g`に対して低エネルギー構成へのスパウンが奨励されます。

# コンストラクタ

  * `GutzwillerSampling(::AbstractHamiltonian, g)`
  * `GutzwillerSampling(::AbstractHamiltonian; g)`

構築後、`G.hamiltonian`で基礎となるハミルトニアンにアクセスでき、`G.g`で`g`パラメータにアクセスできます。

# 例

```jldoctest
julia> H = HubbardMom1D(BoseFS(1,1,1); u=6.0, t=1.0)
HubbardMom1D(fs"|1 1 1⟩"; u=6.0, t=1.0)

julia> G = GutzwillerSampling(H, g=0.3)
GutzwillerSampling(HubbardMom1D(fs"|1 1 1⟩"; u=6.0, t=1.0); g=0.3)

julia> get_offdiagonal(H, BoseFS(2, 1, 0), 1)
(BoseFS{3,3}(1, 0, 2), 2.0)

julia> get_offdiagonal(G, BoseFS(2, 1, 0), 1)
(BoseFS{3,3}(1, 0, 2), 0.8131393194811987)
```

# 観測量

観測量を計算するには、変換されたハミルトニアン`G`を[`AllOverlaps`](@ref)にキーワード引数`transform=G`を使って渡します。

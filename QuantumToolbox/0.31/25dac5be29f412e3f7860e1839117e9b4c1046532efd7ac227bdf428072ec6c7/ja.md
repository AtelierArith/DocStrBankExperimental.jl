```
wigner(
    state::QuantumObject{OpType},
    xvec::AbstractVector,
    yvec::AbstractVector;
    g::Real = √2,
    method::WignerSolver = WignerClenshaw(),
)
```

`state`の[ウィグナー準確率分布](https://en.wikipedia.org/wiki/Wigner_quasiprobability_distribution)を位相空間の点`xvec + 1im * yvec`で生成します。`g`パラメータは、交換関係$[x, y] = i \hbar$における$\hbar$の値に関連するスケーリング因子で、$\hbar=2/g^2$を通じてデフォルト値$\hbar=1$を与えます。

`method`パラメータは、`WignerLaguerre()`または`WignerClenshaw()`のいずれかです。前者はウィグナー関数のラゲール多項式展開を使用し、後者はクレンズホーアルゴリズムを使用します。ラゲール展開はスパース行列に対して高速ですが、クレンズホーアルゴリズムは密な行列に対して高速です。`WignerLaguerre`メソッドにはオプションの`parallel`パラメータがあり、デフォルトは`true`であり、計算を高速化するためにマルチスレッドを使用します。

# 引数

  * `state::QuantumObject`: ウィグナー関数が計算される量子状態。`[`Ket`](@ref)`、`[`Bra`](@ref)`、または`[`Operator`](@ref)`のいずれかです。
  * `xvec::AbstractVector`: 位相空間グリッドのx座標。
  * `yvec::AbstractVector`: 位相空間グリッドのy座標。
  * `g::Real`: 交換関係$[x, y] = i \hbar$における$\hbar$の値に関連するスケーリング因子で、$\hbar=2/g^2$を通じて。
  * `method::WignerSolver`: ウィグナー関数を計算するために使用されるメソッド。`WignerLaguerre()`または`WignerClenshaw()`のいずれかで、デフォルトは`WignerClenshaw()`です。`WignerLaguerre`メソッドにはオプションの`parallel`および`tol`パラメータがあり、それぞれデフォルト値は`true`および`1e-14`です。

# 戻り値

  * `W::Matrix`: 位相空間の点`xvec + 1im * yvec`における状態のウィグナー関数。

# 例

```jldoctest wigner
julia> ψ = fock(10, 0) + fock(10, 1) |> normalize

Quantum Object:   type=Ket()   dims=[10]   size=(10,)
10-element Vector{ComplexF64}:
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im

julia> xvec = range(-5, 5, 200)
-5.0:0.05025125628140704:5.0

julia> wig = wigner(ψ, xvec, xvec);
```

または`WignerLaguerre`メソッドの並列計算を利用する場合

```jldoctest wigner
julia> ρ = ket2dm(ψ) |> to_sparse;

julia> wig = wigner(ρ, xvec, xvec, method=WignerLaguerre(parallel=true));

```

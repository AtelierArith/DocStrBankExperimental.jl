```
AxialAngularMomentumHO(S; z_dim = 3, addr = BoseFS(prod(S))) <: AbstractHamiltonian
```

角運動量演算子は、直交調和振動子基底に適用されます。詳細は [`HOCartesianContactInteractions`](@ref) または [`HOCartesianEnergyConservedPerDim`](@ref) を参照してください。角運動量の `z` 軸への射影を表します：

$$
\hat{L}_z = i \hbar \sum_{j=1}^N \left( b_x b_y^\dag - b_y b_x^\dag \right),
$$

ここで、$b_x^\dag$ と $b_x$ は $x$ 次元の調和振動子のための上昇および下降（はしご）演算子であり、$y$ に対しても同様です。

これは、創造および消滅演算子を持つ $N$ 粒子フォック空間のために実装されています。

$$
\frac{1}{\hbar} \hat{L}_z = i \sum_{n_x=1}^{M_x} \sum_{n_y=1}^{M_y}
    \left( a_{n_x-1,n_y+1}^\dag - a_{n_x+1,n_y-1}^\dag \right) a_{n_x, n_y}.
$$

単位は $\hbar$ です。

引数 `S` は、各次元における直交モードの範囲と、それらのフォック空間モードへのマッピングを定義するタプルです。`S` が 3D システムを示す場合、`z` 次元は `z_dim` を設定することで変更できます。`S` は残りの `x`-`y` 平面で等方的である必要があり、すなわち `S[x_dim] == S[y_dim]` でなければなりません。開始アドレス `addr` は、`num_modes(addr) == prod(S)` を満たす必要があります。

# 例

2D 直交基底における調和振動子状態として解釈される2つのフォックアドレスの重なりを計算します。

```jldoctest
julia> S = (2,2)
(2, 2)

julia> Lz = AxialAngularMomentumHO(S)
AxialAngularMomentumHO((2, 2); z_dim = 3, addr = BoseFS{0,4}(0, 0, 0, 0))

julia> v = DVec(BoseFS(prod(S), 2 => 1) => 1.0)
DVec{BoseFS{1, 4, BitString{4, 1, UInt8}},Float64} with 1 entry, style = IsDeterministic{Float64}()
  fs"|0 1 0 0⟩" => 1.0

julia> w = DVec(BoseFS(prod(S), 3 => 1) => 1.0)
DVec{BoseFS{1, 4, BitString{4, 1, UInt8}},Float64} with 1 entry, style = IsDeterministic{Float64}()
  fs"|0 0 1 0⟩" => 1.0

julia> dot(w, Lz, v)
0.0 + 1.0im
```

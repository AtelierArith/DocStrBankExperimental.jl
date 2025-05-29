```
reduce_wavefunction(Z::Vector{Complex{T}}, grid::CamiDiff.Grid{T}) where T<:Real
```

*通常の* 放射状波動関数 $\tilde{R}_{nl}(ρ)$ から *縮小* 放射状波動関数への変換

$$
    \tilde{\chi}_{nl}(ρ) = ρ \tilde{R}_{nl}(ρ).
$$

ここで $ρ$ は原子核までの放射距離（a.u.単位）です。

#### 例:

```
julia> atom = castAtom(Z=1, A=1, Q=0; msg=false);
julia> spinorbit = castSpinorbit(n=1, ℓ=0; msg=false);
julia> grid = autoGrid(atom, spinorbit, Float64);
julia> RH1s_example = [RH1s(atom.Z, grid.r[n]) for n=1:grid.N];
julia> ZH1s_example = reduce_wavefunction(RH1s_example, grid);
julia> ZH1s_generic = hydrogenic_reduced_wavefunction(atom, spinorbit, grid);
julia> @test ZH1s_example ≈ ZH1s_generic
Test Passed

julia> f1 = real(ZH1s_example);
julia> f2 = real(ZH1s_generic);
julia> compare_functions(f1, f2, 1:grid.N, grid)
```

プロットは `CairomMakie` を使用して作成されます。注意: `compare_functions` は `CamiXon` パッケージには含まれていません。 ![Image](../../assets/compareXH1s.png) ```

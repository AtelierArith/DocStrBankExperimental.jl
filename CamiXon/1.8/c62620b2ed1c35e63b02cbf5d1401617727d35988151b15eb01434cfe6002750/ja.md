```
autoGrid(atom::Atom, T::Type; p=0, rmax=0, nmax=0, N=0, polynom=[], epn=5, k=5, msg=false)
```

与えられた軌道 [`Orbit`](@ref) または軌道の配列 `orbits = [orbit1, orbit2, ⋯]` に対するグリッドパラメータの自動設定。重要なケース：

  * `p == 0` （指数関数的な放射状グリッド）
  * `p == 1` （線形放射状グリッド）
  * `p > 1` （準指数関数的な放射状グリッド）
  * `polynom=[]` （`polynom` に基づく自由多項式グリッド）
  * `Nboost` （数値精度を向上させるための乗数）
  * `epn` （エンドポイント数：台形積分にエンドポイント補正を使用するための奇数）
  * `k` （`k+1` 点アダムス-モールトン積分に使用されるアダムス-モールトンの次数）

#### 例：

```
julia> atom = castAtom(;Z=1, A=1, Q=0, msg=false);

julia> spinorbit = castSpinorbit(n=75, ℓ=0, msg=false);

julia> grid = autoGrid(atom, Float64; nmax=spinorbit.n, msg=true);
Grid: exponential, Float64, rmax = 14137.5, N = 7900, h = 0.00126582, r0 = 0.642684

plot_gridfunction(grid, 1:grid.N; title="")
```

プロットはCairomMakieを使用して作成されます。注意：`plot_gridfunction` は `CamiXon` パッケージの一部ではありません。 ![Image](../../assets/exponential_grid.png)

```
DynamicCoefficient([FT=Float64;] averaging, schedule=IterationInterval(1), minimum_numerator=1e-32)
```

`Smagorinsky`と一緒に使用されると、[BouZeid05](@citet)のスケール不変手法に従って、流れからスマゴリンスキー係数を動的に計算します。

`DynamicCoefficient`は`averaging`手法を必要とし、これは流体パーセルをそのラグランジュ軌道に沿って平均化する`LagrangianAveraging`であるか、選択した次元に沿った方向平均手法を示す整数のタプル（例：`averaging=(1,2)`は`x`および`y`方向の平均を使用）であることができます。

`DynamicCoefficient`は`schedule`に従って更新され、`minimum_numerator`は最終計算の分母で許容される最小値を定義します。

# 例

```jldoctest
julia> using Oceananigans

julia> dynamic_coeff = DynamicCoefficient(averaging=(1, 2))
DynamicCoefficient with
├── averaging = (1, 2)
├── schedule = IterationInterval(1, 0)
└── minimum_numerator = 1.0e-32

julia> dynamic_smagorinsky = Smagorinsky(coefficient=dynamic_coeff)
Smagorinsky closure with
├── coefficient = DynamicCoefficient(averaging = (1, 2), schedule = IterationInterval(1, 0))
└── Pr = 1.0
```

上記の動的スマゴリンスキーは、各タイムステップでその係数が再計算されるため、ほぼ確実に非常に遅くなります。`DynamicCoefficient`計算の高い計算コストを軽減するために、ユーザーは動的係数を時折のみ再計算する近似を導入することができます。これは文献での標準的な慣行であり、原則として係数が単一のタイムステップに比べて比較的遅く変化する限り、任意の頻度の選択が可能ですが、すべての発表された研究は5ステップごとに再計算するようです（例：Bou-Zeid et al. 2005; Chen et al. 2016; Salesky et al. 2017; Chor et al 2021）。この選択は、Bou-Zeid et al. (2005)による結果に由来しているようで、シミュレーションをかなり高速化しながら、各タイムステップの更新頻度と非常に似た結果を生成することがわかりました。ユーザーは`schedule`キーワード引数を使用して更新頻度を変更できます。たとえば、4タイムステップごとに更新される`DynamicCoefficient`は次のように取得されます：

```jldoctest
julia> using Oceananigans

julia> dynamic_coeff = DynamicCoefficient(averaging=(1, 2), schedule=IterationInterval(4))
DynamicCoefficient with
├── averaging = (1, 2)
├── schedule = IterationInterval(4, 0)
└── minimum_numerator = 1.0e-32

julia> dynamic_smagorinsky = Smagorinsky(coefficient=dynamic_coeff)
Smagorinsky closure with
├── coefficient = DynamicCoefficient(averaging = (1, 2), schedule = IterationInterval(4, 0))
└── Pr = 1.0
```

# 参考文献

Bou-Zeid, Elie, Meneveau, Charles, and Parlange, Marc. (2005) A scale-dependent Lagrangian dynamic model for large eddy simulation of complex turbulent flows, Physics of Fluids, **17**, 025105.

Salesky, Scott T., Chamecki, Marcelo, and Bou-Zeid Elie. (2017) On the nature of the transition between roll and cellular organization in the convective boundary layer, Boundary-layer meteorology 163, 41-68.

Chen, Bicheng, Yang, Di, Meneveau, Charles and Chamecki, Marcelo. (2016) Effects of swell on transport and dispersion of oil plumes within the ocean mixed layer, Journal of Geophysical Research: Oceans, 121(5), pp.3564-3578.

Chor, Tomas, McWilliams, James C., Chamecki, Marcelo. (2021) Modifications to the K-Profile Parameterization with nondiffusive fluxes for Langmuir turbulence, Journal of Physical Oceanography, 51(5), pp.1503-1521.

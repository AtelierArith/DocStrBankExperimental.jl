```
TotalLagrangianSPHSystem(initial_condition,
                         smoothing_kernel, smoothing_length,
                         young_modulus, poisson_ratio;
                         n_fixed_particles=0, boundary_model=nothing,
                         acceleration=ntuple(_ -> 0.0, NDIMS),
                         penalty_force=nothing, source_terms=nothing)
```

弾性構造の粒子のためのシステム。

トータルラグランジアンフレームワークが使用されており、支配方程式はすべての関連する量と演算子が初期構成に対して測定されるように定式化されています（O’Connor & Rogers 2021, Belytschko et al. 2000）。手法の詳細については、[Total Lagrangian SPH](@ref tlsph)を参照してください。

# 引数

  * `initial_condition`:  システムの粒子を表す初期条件。
  * `young_modulus`:      ヤング率。
  * `poisson_ratio`:      ポアソン比。
  * `smoothing_kernel`:   このシステムで使用されるスムージングカーネル。                       [Smoothing Kernels](@ref smoothing_kernel)を参照してください。
  * `smoothing_length`:   このシステムで使用されるスムージング長。                       [Smoothing Kernels](@ref smoothing_kernel)を参照してください。

# キーワード引数

  * `n_fixed_particles`:  構造粒子を固定するために使用される固定粒子の数。                       固定粒子は`InitialCondition`の**最後**の粒子である必要があります。下の情報ボックスを参照してください。
  * `boundary_model`: 流体-構造相互作用のために水力学的密度と圧力を計算する境界モデル                   （[Boundary Models](@ref boundary_models)を参照）。
  * `penalty_force`:  大きな変形の下で粒子の位置を正規化するためのペナルティフォース                   （[`PenaltyForceGanzenmueller`](@ref)を参照）。
  * `acceleration`:   システムの加速度ベクトル。（デフォルト：ゼロベクトル）
  * `source_terms`:   このシステムの追加のソース項。デフォルトでは`nothing`                   であるか、または`(coords, velocity, density, pressure)`                   （これらは単一粒子の量）を引数に取り、その粒子の加速度に加算される                   `Tuple`または`SVector`を返す関数である必要があります。                   例えば、[`SourceTermDamping`](@ref)を参照してください。

!!! note
    固定粒子は`InitialCondition`の**最後**の粒子である必要があります。これを行うには、例えば`union`関数を使用します：

    ```jldoctest; output = false, setup = :(fixed_particles = RectangularShape(0.1, (1, 4), (0.0, 0.0), density=1.0); beam = RectangularShape(0.1, (3, 4), (0.1, 0.0), density=1.0))
    solid = union(beam, fixed_particles)

    # output
    ┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
    │ InitialCondition{Float64}                                                                        │
    │ ═════════════════════════                                                                        │
    │ #dimensions: ……………………………………………… 2                                                                │
    │ #particles: ………………………………………………… 16                                                               │
    │ particle spacing: ………………………………… 0.1                                                              │
    └──────────────────────────────────────────────────────────────────────────────────────────────────┘
    ```

    ここで`beam`と`fixed_particles`は`InitialCondition`型です。


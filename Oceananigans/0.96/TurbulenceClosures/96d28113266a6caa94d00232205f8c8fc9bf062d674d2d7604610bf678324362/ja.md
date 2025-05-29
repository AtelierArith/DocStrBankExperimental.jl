```
AnisotropicMinimumDissipation([time_discretization = ExplicitTimeDiscretization, FT = Float64;]
                              C = 1/3, Cν = nothing, Cκ = nothing, Cb = nothing)
```

`AnisotropicMinimumDissipation`乱流閉じ込めの型`FT`のパラメータを返します。

# 引数

  * `time_discretization`: `ExplicitTimeDiscretization()`または`VerticallyImplicitTimeDiscretization()`のいずれかで、                        粘性および拡散フラックスにおける$z$-微分のみを含む項を                        暗黙的な時間離散化で統合します。                        デフォルトは`ExplicitTimeDiscretization()`です。
  * `FT`: 浮動小数点型; デフォルトは`Float64`です。

# キーワード引数

  * `C`: 渦粘性および渦拡散率の両方のポアンカレ定数。`Cν`または`Cκ`が設定されている場合、`C`はそれぞれ渦粘性または渦拡散率のために上書きされます。
  * `Cν`: 運動量渦粘性のためのポアンカレ定数。
  * `Cκ`: トレーサー渦拡散率のためのポアンカレ定数。1つの数または関数の場合、同じ数または関数がすべてのトレーサーに適用されます。`NamedTuple`の場合、すべてのトレーサーのポアンカレ定数を指定するフィールドを持っている必要があります。
  * `Cb`: 浮力修正乗数（`Cb = nothing`は無効にし、`Cb = 1`は[Abkar16](@citet)によって使用されました）。       *注意*: この浮力修正項を計算する前に、水平平均成分を*引き算しない*ことに注意してください。この実装は[Abkar16](@citet)の提案と異なり、この近似の影響はテストまたは検証されていません。

デフォルトでは、`C = Cν = Cκ = 1/3`、および`Cb = nothing`で、浮力修正項は無効になります。デフォルトのポアンカレ定数は、2次の輸送スキームを仮定して、サブグリッドスケールエネルギー生成を離散化することによって見つかります。[Verstappen14](@citet)は、ポアンカレ定数は単純な（スペクトル）離散化の4倍大きいべきであり、私たちの定式化では`C = 1/3`となることを示しています。彼らはまた、この係数が正しい離散的生成-消散バランスを生み出すことを経験的に示しました。私たちはさらにこれをhttps://github.com/CliMA/Oceananigans.jl/issues/4367で示しました。

`C`、`Cν`および`Cκ`は、数値または`x, y, z`の関数である可能性があります。

# 例

```jldoctest
julia> using Oceananigans

julia> pretty_diffusive_closure = AnisotropicMinimumDissipation(C=1/2)
AnisotropicMinimumDissipation{ExplicitTimeDiscretization}乱流閉じ込め:
           運動量渦粘性のためのポアンカレ定数 Cν: 0.5
    トレーサーの渦拡散率のためのポアンカレ定数 Cκ: 0.5
                        浮力修正乗数 Cb: nothing
```

```jldoctest
julia> using Oceananigans

julia> const Δz = 0.5; # 表面でのグリッド解像度

julia> surface_enhanced_tracer_C(x, y, z) = 1/12 * (1 + exp((z + Δz/2) / 8Δz));

julia> fancy_closure = AnisotropicMinimumDissipation(Cκ=surface_enhanced_tracer_C)
AnisotropicMinimumDissipation{ExplicitTimeDiscretization}乱流閉じ込め:
           運動量渦粘性のためのポアンカレ定数 Cν: 0.3333333333333333
    トレーサーの渦拡散率のためのポアンカレ定数 Cκ: surface_enhanced_tracer_C
                        浮力修正乗数 Cb: nothing
```

```jldoctest
julia> using Oceananigans

julia> tracer_specific_closure = AnisotropicMinimumDissipation(Cκ=(c₁=1/12, c₂=1/6))
AnisotropicMinimumDissipation{ExplicitTimeDiscretization}乱流閉じ込め:
           運動量渦粘性のためのポアンカレ定数 Cν: 0.3333333333333333
    トレーサーの渦拡散率のためのポアンカレ定数 Cκ: (c₁ = 0.08333333333333333, c₂ = 0.16666666666666666)
                        浮力修正乗数 Cb: nothing
```

# 参考文献

Verstappen, R., Rozema, W., and Bae, J. H. (2014), "Numerical scale separation in large-eddy     simulation", Center for Turbulence ResearchProceedings of the Summer Program 2014.

Vreugdenhil C., and Taylor J. (2018), "Large-eddy simulations of stratified plane Couette     flow using the anisotropic minimum-dissipation model", Physics of Fluids 30, 085104.

Verstappen, R. (2018), "How much eddy dissipation is needed to counterbalance the nonlinear     production of small, unresolved scales in a large-eddy simulation of turbulence?",     Computers & Fluids 176, pp. 276-284. ```

```
SplitExplicitFreeSurface(grid = nothing;
                         gravitational_acceleration = g_Earth,
                         substeps = nothing,
                         cfl = nothing,
                         fixed_Δt = nothing,
                         averaging_kernel = averaging_shape_function,
                         timestepper = ForwardBackwardScheme())
```

`gravitational_acceleration`を用いた自由表面ダイナミクスの明示的時間離散化を表す`SplitExplicitFreeSurface`を返します。自由表面ダイナミクスは次のように離散化されて解かれます：

$$
\begin{gather}
∂_t η = - \nabla ⋅ U, \\
∂_t U = - g H \nabla η + G^U,
\end{gather}
$$

ここで、$η$は自由表面の変位、$U$はバロトロピック速度ベクトルで、速度場$u$と$v$の垂直積分として計算され、$H$はコラムの深さ、$G^U$は$u$と$v$の傾向の積分として計算され、$g$は重力加速度です。

離散化された方程式は、サブステップ$Δτ < Δt$を用いてバロクリニックタイムステップ（$Δt$）内で解かれます。バロトロピック速度はサブステッピングを通じてフィルタリングされ、最終的に新しいタイムステップでの速度のバロトロピックモードはフィルタリングされた速度で修正されます。

# キーワード引数

  * `gravitational_acceleration`: 重力加速度（デフォルト: `g_Earth`）
  * `substeps`: 範囲`(t, t + 2Δt)`を分割するサブステップの数。ここで、`Δt`はバロクリニックタイムステップです。いくつかの平均化関数は`2Δt`までサブステッピングを必要としないことに注意してください。サブステップの数は、`averaging_kernel > 0`である`averaging_kernel`の最後のインデックスに自動的に減少します。
  * `cfl`: 設定されている場合、バロトロピック重力波速度から課せられる移流時間スケールに基づいて`substeps`の数が計算されます。`fixed_Δt`が提供されている場合、`substeps`の数は正確な`cfl`を維持するように適応します。そうでない場合、バロクリニックタイムステップが`Δt_baroclinic < fixed_Δt`を満たす限り、実効cflは指定された`cfl`より常に低くなります。

!!! info "必要なキーワード引数"
    `substeps` *または* `cfl`のいずれかを指定する必要があります。

    `cfl`が指定されている場合、`grid`も位置引数として必要です。


  * `fixed_Δt`: 許可される最大バロクリニックタイムステップ。`fixed_Δt`が`nothing`であり、cflが提供されている場合、サブステップの数はバロクリニックタイムステップから動的に計算され、一定のcflを維持します。
  * `averaging_kernel`: バロトロピック輸送`U`と自由表面`η`をバロトロピック進行内で平均化するために使用される`τ`の関数。`τ`は0から2までの分数サブステップで、バロクリニックタイムステップ`t + Δt`は`τ = 1`に位置します。`averaging_kernel`関数は`τ = 1`で中心に配置されるべきであり、すなわち、$∑ (aₘ m / M) = 1$、ここで、合計は$m = 1, ..., M_*$の範囲で行われます。ここで、$m = 0$と$m = M$は、バロトロピックタイムステッピングが行われる2つの連続したバロクリニックタイムステップに対応し、$M_*$は`averaging_kernel > 0`である最後のバロトロピックタイムステップに対応します。デフォルトでは、[Shchepetkin2005](@citet)によって説明された平均化カーネルが使用されます。
  * `timestepper`: バロトロピック進行に使用される時間ステッピングスキーム。次のいずれかを選択します：

      * `ForwardBackwardScheme()`（デフォルト）：`η = f(U)` その後 `U = f(η)`、
      * `AdamsBashforth3Scheme()`：`η = f(U, Uᵐ⁻¹, Uᵐ⁻²)` その後 `U = f(η, ηᵐ, ηᵐ⁻¹, ηᵐ⁻²)`。

# 参考文献

Shchepetkin, A. F., & McWilliams, J. C. (2005). The regional oceanic modeling system (ROMS): a split-explicit, free-surface, topography-following-coordinate oceanic model. Ocean Modelling, 9(4), 347-404. ```

```
synthesize(atm, linelist, A_X, (λ_start, λ_stop); kwargs... )
synthesize(atm, linelist, A_X, wavelength_ranges; kwargs... )
```

合成スペクトルを計算します。 [`SynthesisResult`](@ref) を返します。

# 引数

  * `atm`: モデル大気（[`read_model_atmosphere`](@ref）を参照）
  * `linelist`: [`Line`](@ref) のベクトル（[`read_linelist`](@ref)、[`get_APOGEE_DR17_linelist`](@ref)、および [`get_VALD_solar_linelist`](@ref）を参照）
  * `A_X`: 水素からウランまでの元素の A(X) 豊富さ (log(X/H) + 12) を含むベクトル。（[`format_A_X`](@ref）を参照）
  * スペクトルを合成する波長。 `(λstart, λstop)` のペアとして指定するか、`[(λstart1, λstop1), (λstart2, λstop2), ...]` のペアのリストとして指定できます。
  * `λ_start`: 合成したい領域の下限（Å単位）。
  * `λ_stop`: 合成したい領域の上限（Å単位）。
  * `λ_step`（デフォルト: 0.01）: （おおよその）ステップサイズ（Å単位）。

# 例

5000 Å と 5100 Å の間のスペクトルを合成し、すべての金属の豊富さを太陽値よりも0.5デックス少なく設定し、炭素だけを [C/H]=-0.25 に設定するには：

```
atm = read_model_atmosphere("path/to/atmosphere.mod")
linelist = read_linelist("path/to/linelist.vald")
A_X = format_A_X(-0.5, Dict("C" => -0.25))
result = synthesize(atm, linelist, A_X, 5000, 5100)
```

# オプションの引数：

  * `vmic`（デフォルト: 0）は、マイクロタービュレント速度 $\xi$（km/s単位）。
  * `line_buffer`（デフォルト: 10）: 提供された波長範囲から線がどれだけ遠くにあっても許容される最大距離（Å単位）。ウィンドウの端が強い線の近くにある場合は、これを上げる必要があるかもしれません。
  * `cntm_step`（デフォルト 1）: 連続体不透明度が計算される点間の距離（Å単位）。
  * `hydrogen_lines`（デフォルト: `true`）: 合成にH線を含めるかどうか。
  * `use_MHD_for_hydrogen_lines`（デフォルト: `true`）: 水素線に対してMHD占有確率形式を使用するかどうか。（水素の束縛自由吸収には常にMHDが使用されます。）
  * `hydrogen_line_window_size`（デフォルト: 150）: 各水素線中心からの最大距離（Å単位）で、総吸収係数への寄与を計算します。
  * `mu_values`（デフォルト: 20）: 表面フラックスを計算するμ値の数、または球面幾何学で転送を行う際に使用する特定の値のベクトル。`mu_points`が整数の場合、値はガウス・レジェンドル積分ごとに選択されます。直接指定されている場合、天体物理フラックスのために台形法が使用されます。デフォルト値は10^-3レベルの精度に十分です。デフォルトの放射伝達スキームを使用している場合、平行平面モデル大気でのμの積分は正確であるため、このパラメータは影響を与えません。ポイントと重みは出力の`mu_grid`フィールドに返されます。
  * `line_cutoff_threshold`（デフォルト: `3e-4`）: 線プロファイルが切り捨てられる連続体吸収係数の割合。この値は、線吸収計算が合成を支配するため、パフォーマンスに大きな影響を与えます。実行時間を犠牲にして精度を高めるために、これを下げてください。デフォルト値は10^-3レベル以下の最終スペクトルに影響を与えるはずです。
  * `electron_number_density_warn_threshold`（デフォルト: `Inf`）: 計算された電子数密度と入力された電子数密度の相対差がこの値を超える場合、警告が表示されます。デフォルトでは、この警告は抑制されます（閾値は`Inf`）ので、観測上の結果に影響を与えない場合に簡単に発生します。以下の`electron_number_density_warn_min_value`も参照してください。
  * `electron_number_density_warn_min_value`（デフォルト: `1e-4`）: 警告が表示される電子数密度と総数密度の比の最小値。
  * `return_cntm`（デフォルト: `true`）: 各波長で連続体を返すかどうか。これがfalseの場合、`solution.cntm`は`nothing`になります。
  * `ionization_energies`、`Species`をその最初の3つのイオン化エネルギーにマッピングする`Dict`、デフォルトは`Korg.ionization_energies`。
  * `partition_funcs`、`Species`を分配関数（ln(T)の形式）にマッピングする`Dict`。デフォルトはBarklem & Collet 2016のデータ、`Korg.default_partition_funcs`。
  * `equilibrium_constants`、二原子分子を表す`Species`を部分圧形式の分子平衡定数の10進対数にマッピングする`Dict`。デフォルトはBarklemとCollet 2016のデータ、`Korg.default_log_equilibrium_constants`。
  * `use_chemical_equilibrium_from`（デフォルト: `nothing`）: `synthesize`によって返された別の解を取ります。提供されると、化学平衡解はこのオブジェクトから取得され、再計算されません。これは、豊富さ`A_X`とモデル大気`atm`が変更されていない場合にのみ物理的に自己整合的です。
  * `molecular_cross_sections`（デフォルト: `[]`）: 事前計算された分子断面積のベクトル。これを生成する方法については[`MolecularCrossSection`](@ref)を参照してください。デフォルトの放射伝達スキームを使用している場合、分子断面積はリストが5000 Åをカバーしている場合にのみカバーする必要があります。
  * `tau_scheme`（デフォルト: "linear"）: 光学的深さを計算する方法。オプションは "linear" と "bezier"（テストのみ - 推奨されません）。
  * `I_scheme`（デフォルト: `"linear_flux_only"`）: 強度を計算する方法。オプションは `"linear"`、`"linear_flux_only"`、および `"bezier"`。`"linear_flux_only"` は最も速いですが、大気の上部以外では強度値を返しません。"linear" は同等の計算を行いますが、すべての層で強度を保存します。`"bezier"` はテスト用であり、推奨されません。
  * `verbose`（デフォルト: `false`）: 進行状況などの情報を表示するかどうか。

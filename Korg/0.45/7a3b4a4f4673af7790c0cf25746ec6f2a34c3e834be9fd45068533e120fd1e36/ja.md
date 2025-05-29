```
interpolate_marcs(Teff, logg, A_X; kwargs...)
interpolate_marcs(Teff, logg, m_H=0, alpha_m=0, C_m=0; kwargs...)
```

MARCSからモデル大気を補間して計算します（(Gustafsson+ 2008)[https://ui.adsabs.harvard.edu/abs/2008A&A...486..951G/abstract]）。`Teff`と`logg`に加えて、大気は`m_H`、`alpha_m`、および`C_m`によって指定され、これらは`A_X`豊富さベクトルから自動的に決定できます（推奨方法、[`format_A_X`](@ref)を参照）。MARCS大気モデルはGrevesse+ 2007の太陽豊富さ（`Korg.grevesse_2007_solar_abundances`）を用いて構築されていることに注意してください。`A_X`が提供されると、自動的に処理されます。

`interpolate_marcs`は、異なる星のパラメータ領域に対して3つの異なる補間スキームを使用します。標準的なケースでは、モデル大気グリッドは[SDSS用に生成されたもの](https://dr17.sdss.org/sas/dr17/apogee/spectro/speclib/atmos/marcs/MARCS_v3_2016/Readme_MARCS_v3_2016.txt)であり、変換されて線形補間されています。冷たい矮星（`Teff` ≤ 4000 K、`logg` ≥ 3.5）の場合、グリッドは不変の`tau_5000`値に再サンプリングされ、三次スプラインで補間されます。低金属量モデル（-5 ≤ `m_H` < -2.5）の場合、標準組成（すなわち固定されたalphaとC）の大気のグリッドが使用されます。（微小乱流は矮星の場合1km/s、巨星の場合2km/sであり、球状モデルの質量は1太陽質量です。）補間方法は標準的なケースと同じです。モデル大気補間によって導入される誤差についての詳細と議論については[Wheeler+ 2024](https://ui.adsabs.harvard.edu/abs/2023arXiv231019823W/abstract)を参照してください。（冷たい矮星のための三次スキームは論文では未実装とされていますが、現在は利用可能です。）

# キーワード引数

  * `spherical`: ShellAtmosphereを返すかどうか（PlanarAtmosphereではなく）。デフォルトは`logg` < 3.5のときはtrueです。
  * `solar_abundances`: （デフォルト: `grevesse_2007_solar_abundances`）`M_H`、`alpha_M`、および`C_M`の代わりに`A_X`が提供される場合に使用する太陽豊富さ。デフォルトは大気グリッドのものと一致するように選ばれており、これを変更すると他の何かを試みている可能性があります。
  * `clamp_abundances`: （デフォルト: `false`）`A_X`を指定する場合のみ許可されます。豊富さパラメータを範囲内に制限するかどうか、範囲外エラーを避けるため。
  * `perturb_at_grid_values`（デフォルト: `true`）：グリッド値に正確にある各パラメータに非常に小さな数を加えたり引いたりするかどうか。これにより、最小化器に問題を引き起こす可能性のあるゼロ導関数を防ぎます。
  * `resampled_cubic_for_cool_dwarfs`（デフォルト: `true`）：冷たい矮星のための特別な方法を使用するかどうか。
  * `archives`: 使用する大気グリッドを含むタプル。テスト目的のため。

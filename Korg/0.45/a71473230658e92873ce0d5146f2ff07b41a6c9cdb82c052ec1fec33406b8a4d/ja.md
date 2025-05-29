```
load_ExoMol_linelist(specs, states_file, transitions_file, upper_wavelength, lower_wavelength)
```

ExoMolからリストを読み込みます。[`Line`](@ref)のベクターを返し、[`read_linelist`](@ref)と同じです。

# 引数

  * `spec`: 種、すなわちリストが対象とする分子
  * `states_file`: ExoMolの状態ファイルへのパス
  * `transitions_file`: ExoMolの遷移ファイルへのパス
  * `upper_wavelength`: 読み込む波長範囲の上限（Å）
  * `lower_wavelength`: 読み込む波長範囲の下限（Å）

# キーワード引数

  * `line_strength_cutoff`: リストをフィルタリングするために使用される線強度のカットオフ（デフォルト: -15）。詳細については[`approximate_line_strength`](@ref)を参照してください。
  * `T_line_strength`: 線強度を評価する温度（K）（デフォルト: 3500.0）

!!! warning
    この機能はベータ版です。


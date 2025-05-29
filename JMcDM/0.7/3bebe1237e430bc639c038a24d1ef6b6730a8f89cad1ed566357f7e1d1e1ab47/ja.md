```
mcdm(setting, method = TopsisMethod())

与えられた意思決定行列、重みベクトル、および関数リストに対して選択した方法を実行します。
```

# 引数:

  * `setting::MCDMSetting`: 意思決定行列、重みベクトル、および関数を保持するMCDMSettingオブジェクト。
  * `method::MCDMMethod`: 好ましいMCDMMethod。デフォルトはTopsisMethod()です。

# 説明

このメソッドはMCDMMethod型のサブタイプの1つです。例を参照してください。

# 出力

  * `::MCDMResult`: MCDMResult型のサブタイプから派生したオブジェクト。

# 例

```julia-repl
julia> # mcdm() for Topsis:
julia> # mcdm(setting, TopsisMethod())

julia> # mcdm() for Saw:
julia> # mcdm(setting, SawMethod())

julia> # mcdm() with optional parameters:
julia> # mcdm(setting, GreyMethod(0.6))
```

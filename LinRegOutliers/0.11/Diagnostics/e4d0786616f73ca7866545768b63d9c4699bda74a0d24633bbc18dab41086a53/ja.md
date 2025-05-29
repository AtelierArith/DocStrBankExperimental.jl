```
dfbeta(setting, omittedIndex)
```

与えられた回帰設定と観察インデックスに対してDFBETA診断を適用します。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `omittedIndex::Int`: 除外された観察のインデックス。

# 例

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> dfbeta(setting, 1)
2-element Vector{Float64}:
  9.643915678524024
 -0.14686166007904422
```

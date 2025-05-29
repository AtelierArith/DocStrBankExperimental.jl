```
covratio(setting, omittedIndex)
```

与えられた回帰設定と観察インデックスに対して共分散比診断を適用します。

# 引数

  * `setting::RegressionSetting`: 回帰設定オブジェクト。
  * `omittedIndex::Int`: 除外された観察のインデックス。

# 例

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> covratio(setting, 1)
1.2945913799871505
```

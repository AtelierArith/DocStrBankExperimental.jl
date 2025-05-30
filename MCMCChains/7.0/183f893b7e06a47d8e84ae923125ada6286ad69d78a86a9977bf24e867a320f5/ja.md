```
summarize(chains, funs...[; sections, func_names = [], name = "", append_chains = true])
```

`chains`を`ChainsDataFrame`で要約します。

# 例

  * `summarize(chns)` : 完全なチェーンの要約
  * `summarize(chns[[:parm1, :parm2]])` : 選択したパラメータのチェーン要約
  * `summarize(chns; sections=[:parameters])`  : :parametersセクションのチェーン要約
  * `summarize(chns; sections=[:parameters, :internals])` : 複数のセクションのチェーン要約

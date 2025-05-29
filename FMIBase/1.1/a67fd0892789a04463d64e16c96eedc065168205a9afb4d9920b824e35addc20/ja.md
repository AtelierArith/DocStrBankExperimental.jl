```
getInitial(mv::fmi2ScalarVariable)
```

対応するモデル変数の `inital` エントリを返します。

# 引数

  * `fmi2GetStartValue(mv::fmi2ScalarVariable)`: “ModelVariables” 要素は、順序付けられた “ScalarVariable” 要素の集合で構成されています。“ScalarVariable” は、実数や整数変数のような原始型の変数を表します。

# 返り値

  * `mv.Real.unit`: 原始型 Real を表す対応する ScalarVariable の `inital` エントリを返します。それ以外の場合は `nothing` が返されます。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2: 2.2.7 モデル変数の定義 (ModelVariables)

```

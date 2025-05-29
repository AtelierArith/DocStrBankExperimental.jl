```
getDeclaredType(md::fmi2ModelDescription, mv::fmi2ScalarVariable)
```

対応するモデル変数 `mv` の `fmi2SimpleType` を `md.typeDefinitions` に定義された通りに返します。`mv` に宣言された型がない場合は `nothing` を返します。`mv` に宣言された型があるが見つからない場合は、警告を発し `nothing` を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。
  * `mv::fmi2ScalarVariable`: “ModelVariables” 要素は、順序付けられた “ScalarVariable” 要素の集合から成ります。“ScalarVariable” は、実数や整数変数のような原始型の変数を表します。

# 出典

  * FMISpec2.0.3 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.3: 2.2.7 モデル変数の定義 (ModelVariables)

```
replace_variables!(model, throw = true, varname = vardef, varname2 = vardef2)
```

モデル内の既存の変数（主変数、副変数、またはパラメータ）を新しい定義に置き換えます。

# 引数

  * `model`: 変数を置き換えるインスタンス
  * `varname=vardef::JutulVariables`: `varname` の変数を `vardef` で置き換えます
  * `throw=true`: 指定された変数定義が主変数または副変数に見つからない場合はエラーをスローし、それ以外の場合は静かに `model` を返します。

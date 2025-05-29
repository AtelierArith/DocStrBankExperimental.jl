```
simshow(arr; set_zero=false, set_one=false, γ=1, cmap=:gray)
```

実数値配列を表示します。JupyterおよびPluto内で動作します。

# キーワード引数

変換はその順序で適用されます。

  * `set_zero=false` は最小値を引いて最小値を0に設定します
  * `set_one=true` は最大値で割って最大値を1に設定します
  * `γ` はガンマ補正を適用します
  * `cmap=:gray` はColorSchemes.jlによって提供されるカラーマップを適用します。 `cmap=:gray` の場合は単に `Colors.Gray` が使用され、異なるカラーマップでは結果は `Colors.RGB` 要素型になります。 `:jet`、`:deep`、`thermal` など、ColorSchemes.jlのカタログを読んで異なるものを試すことができます。

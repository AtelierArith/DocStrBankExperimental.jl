```
goto(page::Page, url::String; verbose::Bool=false)
```

指定されたURLに移動し、ページの読み込みを待ちます。

# 引数

  * `page::Page`: 移動するページ
  * `url::String`: 移動するURL
  * `verbose::Bool`: 詳細なログを有効にする（デフォルト: false）

# 例外

  * `NavigationError`: ナビゲーションが失敗するか、タイムアウトした場合

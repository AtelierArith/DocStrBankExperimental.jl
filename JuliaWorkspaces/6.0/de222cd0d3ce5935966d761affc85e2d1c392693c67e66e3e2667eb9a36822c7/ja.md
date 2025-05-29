```
get_julia_syntax_tree(jw::JuliaWorkspace, uri::URI)
```

ワークスペースからJuliaファイルの構文木を取得します。

# 戻り値

  * タプル `(tree, diagnostics)`。ここで、`tree` は構文木であり、`diagnostics` は `Diagnostic` 構造体のベクターです。

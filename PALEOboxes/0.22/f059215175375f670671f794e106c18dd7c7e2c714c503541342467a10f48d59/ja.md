```
check_variable_links(model, modeldata; [throw_on_error=true] [, expect_hostdep_varnames=["global.tforce"]]) -> links_ok::Bool
```

すべての変数が正しくリンクされているかを確認します。予期しないホスト依存の非状態変数（つまり、リンクされていない変数）がないことを確認します。

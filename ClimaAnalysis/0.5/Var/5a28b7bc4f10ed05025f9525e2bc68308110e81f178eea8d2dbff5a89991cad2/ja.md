```
resampled_as(src_var::OutputVar, dest_var::OutputVar, dim_names = nothing)
```

`src_var`の`data`を`dest_var`の`dims`に再サンプリングします。

ここで行われる再サンプリングは1次線形再サンプリングです。

文字列または反復可能な`dim_names`が`nothing`の場合、すべての次元に対して再サンプリングが行われます。それ以外の場合、`dim_names`に指定された次元に対して再サンプリングが行われます。

!!! note "自動的な次元の再配置"
    すべての次元に対して再サンプリングが行われる場合、結果の`OutputVar`の次元の再配置は自動的に行われます。


再サンプリングを行う正しい次元は`conventional_dim_name`を使用して特定されます。たとえば、`src_var`に`lon`という名前の経度次元があり、`dest_var`に`long`という名前の経度次元があり、`dim_names`が`longitude`の場合、再サンプリングは経度次元で行われます。なぜなら、`conventional_dim_name`が`lon`、`long`、および`longitude`を`longitude`にマッピングするからです。

!!! compat "`dim_names`キーワード引数"
    キーワード引数`dim_names`はClimaAnalysis v0.5.14で導入されました。


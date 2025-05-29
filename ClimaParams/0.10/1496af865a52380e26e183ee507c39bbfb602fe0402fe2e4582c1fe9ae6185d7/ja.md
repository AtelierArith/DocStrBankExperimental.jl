```
log_parameter_information(
    pd::AbstractTOMLDict,
    filepath;
    strict::Bool = false
)
```

`filepath`にパラメータログファイルを書き込みます。オーバーライドパラメータがすべて使用されているかを確認します。

`strict = true`の場合、オーバーライドパラメータが未使用の場合はエラーになります。

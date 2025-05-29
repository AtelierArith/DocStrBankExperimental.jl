```
changepassword(client::PCloudClient; kwargs...)
```

現在のユーザーのパスワードを変更します

`oldpassword` にはユーザーの古いパスワードを含める必要があり、`newpassword` を指定してユーザーのパスワードを変更します。

新しいパスワードは、少なくとも6文字の長さで、少なくとも4つの異なる文字を含む必要があり、すべての文字が連続していることはできません（アルファベットまたは数字のいずれか、次のいずれも無効です 'abcdef', '123456', '987654'）また、標準的なキーボードのすべての連続した文字で始まったり終わったりすることはできません（'qwerty' や 'poiuyt' は無効です）。また、パスワードは空白で始まったり終わったりすることはできません。

出典: https://docs.pcloud.com/methods/auth/changepassword.html

# 引数

  * `oldpassword::String`: ユーザーの現在のパスワード
  * `newpassword::String`: 現在のパスワードを上書きする希望のパスワード

# 出力例

```
{
    "result": 0
}
```

Quandlユーザーアカウントの認証を設定します。Quandl APIキーを渡して一度実行すると、将来の使用のために保存されます。

```
quandl_auth(key::String=""; authfile::String=joinpath(homedir(),"quandl-auth"))::String
```

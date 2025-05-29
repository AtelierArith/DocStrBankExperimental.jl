```
setup(;
    login     :: AbstractString = "",
    password  :: AbstractString = "",
    overwrite :: Bool = false
)
```

あなたの.dodsrcおよび.netrcファイルを設定する関数です。 `login`および`password`のキーワード引数を提供しない場合、.netrcファイルは作成されません。

# キーワード引数

  * `login` : あなたのEarthdataユーザー名。 `login`と`password`の両方の引数を指定する必要があります。
  * `password` : あなたのEarthdataパスワード。 `login`と`password`の両方の引数を指定する必要があります。
  * `overwrite` : `true`の場合、既存の.dodsrcおよび.netrcファイルを提供されたデータで上書きします。

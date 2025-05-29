```
C_iio_create_default_context()
```

ローカルまたはリモートIIOデバイスからコンテキストを作成します。

# 戻り値

  * 成功した場合、iio_context構造体へのポインタ
  * 失敗した場合、アサーションが有効になっているとエラーがスローされます
  * 失敗した場合、アサーションが無効になっているとNULLが返されます

# 注意

この関数は、IIOD_REMOTE環境変数がIIODサーバーが実行されているホスト名に設定されている場合、ネットワークコンテキストを作成します。空の文字列に設定されている場合、サーバーはZeroConfを使用して発見されます。環境変数が設定されていない場合、代わりにローカルコンテキストが作成されます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#ga21076125f817a680e0c01d4a490f0416)

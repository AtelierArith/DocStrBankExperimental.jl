```
ConnContext
```

永続的なFTP接続を追跡します。

# 引数

  * `url::AbstractString`: FTPサーバーのURL。
  * `options::RequestOptions`: 接続に使用されるオプション。

# キーワード

  * `verbose::Union{IOStream,Bool}=false`: LibCURLの出力をキャプチャするための`IOStream`または`Bool`。trueの場合、出力はSTDERRに書き込まれます。

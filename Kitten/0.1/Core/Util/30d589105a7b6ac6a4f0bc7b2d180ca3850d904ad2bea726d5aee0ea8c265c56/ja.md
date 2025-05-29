```
file(filepath::String; loadfile=nothing, status = 200, headers = []) :: HTTP.Response
```

ファイルを読み込み、HTTP.Responseを返します。ファイルはバイナリとして読み込まれます。ファイルが存在しない場合、ArgumentErrorがスローされます。MIMEタイプとファイルのサイズがヘッダーに追加されます。

# 引数

  * `filepath`: 読み込むファイルへのパス。
  * `loadfile`: ファイルを読み込むためのオプションの関数。指定されていない場合、ファイルは`open`関数を使用して読み込まれます。
  * `status`: レスポンスに使用されるHTTPステータスコード。デフォルトは200です。
  * `headers`: レスポンスに含める追加のヘッダー。デフォルトは空の配列です。

# 戻り値

  * HTTPレスポンス。

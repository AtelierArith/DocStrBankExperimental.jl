```
aws_http_header_compression
```

ヘッダーの文字列がリテラル文字列をエンコードするのではなく、キャッシュ内の文字列のインデックスをエンコードすることによって圧縮されるかどうかを制御します。

この設定はHTTP/1.x接続には影響しません。HTTP/2接続では、これがHPACKの動作を制御します。セキュリティに関する考慮事項についてはRFC-7541のセクション7.1を参照してください。

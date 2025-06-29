```
C_iio_create_context_from_uri(uri)
```

URI記述からコンテキストを作成します。

# パラメータ

  * `uri::String` : コンテキストの場所を記述するURI

# 戻り値

  * 成功した場合、iio_context構造体へのポインタ
  * 失敗した場合、アサーションが有効になっているとエラーがスローされます。
  * 失敗した場合、アサーションが無効になっているとNULLが返されます。

# 注意

以下のURIは、コンパイル時のバックエンドサポートに基づいてサポートされています：

  * ローカルバックエンド、"local:" : アドレス部分を持ちません。例えば "local:"
  * XMLバックエンド、"xml:" : アドレス部分にXMLファイルへのパスが必要です。例えば "xml:/home/user/file.xml"
  * ネットワークバックエンド、"ip:" : 特定の実行中のIIOデーモンに接続するためのホスト名、IPv4、またはIPv6が必要です。または、ライブラリがZeroConfサポートでコンパイルされている場合、自動発見のためにアドレス部分を持たないことも可能です。例えば "ip:192.168.2.1"、または "ip:localhost"、または "ip:"、または "ip:plutosdr.local"
  * USBバックエンド、"usb:" : 1つ以上のUSBデバイスが接続されている場合、バス、アドレス、およびインターフェース部分をドットで区切る必要があります。例えば "usb:3.32.5"。1つのUSBデバイスのみが接続されている場合は、短縮形 "usb:" を使用できます。
  * シリアルバックエンド、"serial:" は次のものを必要とします：

      * ポート (/dev/ttyUSB0),
      * ボーレート (デフォルト115200)
      * シリアルポートの設定

          * データビット (5 6 7 8 9)
          * パリティ ('n' なし, 'o' 奇数, 'e' 偶数, 'm' マーク, 's' スペース)
          * ストップビット (1 2)
          * フロー制御 (' ' なし, 'x' Xon Xoff, 'r' RTSCTS, 'd' DTRDSR)
      * 例えば "serial:/dev/ttyUSB0,115200" または "serial:/dev/ttyUSB0,115200,8n1"

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gafdcee40508700fa395370b6c636e16fe)

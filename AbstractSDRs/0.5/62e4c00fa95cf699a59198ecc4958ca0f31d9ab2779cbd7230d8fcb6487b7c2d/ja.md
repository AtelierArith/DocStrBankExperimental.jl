スキャンインターフェースと見つかったSDRを返します

# –– 構文

sdr = scan()  sdr = scan(backend;key...)

# 入力パラメータ

関数がパラメータなしで呼び出されると、UHDBindingsやAdalmPlutoなどの利用可能なすべてのバックエンドを検索します。そうでない場合、検索は希望するバックエンドに制限されます。オプションの引数は、UHDBindingsおよびAdalmPlutoによってサポートされているものです。UHDBindingsの`uhd_find_devices()`およびAdalmPlutoの`scan`関数を参照してください。

# キーワード

  * args : UHDバックエンドでUSRP IPアドレスを指定するために使用される文字列。例: scan(:uhd;args="addr=192.168.10.16")
  * backend : Plutoバックエンドで使用されるインターフェースを指定するために使用される文字列 ("local", "xml", "ip", "usb")

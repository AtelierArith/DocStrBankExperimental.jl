```
mutable struct TLSConnectionOptions
    ptr::Ref{aws_tls_connection_options}
end
```

接続特有のTLSオプション。このオブジェクトは安価ですが、TLSコンテキストは高価なオブジェクトであることに注意してください。

高度な使用に関する注意: この構造体の内部コンストラクタはデフォルトのままにされているため、必要に応じて独自のネイティブデータを持ち込むことができます。ただし、そのデータのメモリ管理はあなたの責任となります。

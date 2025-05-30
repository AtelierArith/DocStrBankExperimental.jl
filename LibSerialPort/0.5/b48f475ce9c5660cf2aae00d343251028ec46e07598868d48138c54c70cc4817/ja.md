```
print_port_metadata(sp::SerialPort; show_config::Bool = true)
```

このポートに関する情報を表示します。注意: フィールドにアクセスする前に、ポートを開いて有効なFD/ハンドルを取得する必要があります。

`show_config`はデフォルトで`true`であり、現在のポート設定を出力します。

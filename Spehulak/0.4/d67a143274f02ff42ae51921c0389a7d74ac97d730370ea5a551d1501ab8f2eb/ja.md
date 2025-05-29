```
launch(
    port::Int = 9001, host::String = "127.0.0.1";
    async::Bool = true)
```

ブラウザでSpehulakを起動します。

デフォルトは: `http://127.0.0.1:9001`。これは`Genie.up`の便利なラッパーであり、サーバーの設定をカスタマイズするには`Genie.up()`と`Genie.config`を使用します。

# 引数

  * `port::Int = 9001`: サーバーを起動するポート。
  * `host::String = "127.0.0.1"`: サーバーを起動するホスト。
  * `async::Bool = true`: サーバーを非同期に起動するかどうか、つまりバックグラウンドで起動するかどうか。

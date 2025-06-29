```
StreamOutlet(info; chunk_size = 0, max_buffered = 360)
```

新しいストリームアウトレットを確立します。これにより、ストリームが発見可能になります。

# 引数

  * `info::StreamInfo`: このストリームを作成するために使用するストリーム情報。アウトレットのライフタイムにわたって一定です。

# キーワード引数

  * `chunk_size::Integer`: 送信のための希望するチャンクの粒度（サンプル単位）。0として指定された場合、各プッシュ操作は1つのチャンクを生成します。ストリームの受信者はこの設定をバイパスすることができます。
  * `max_buffered::Integer`: バッファリングするデータの最大量（名目上のサンプリングレートがある場合は秒単位、そうでない場合はサンプル単位でx100）。良いデフォルトは360で、これは6分のデータに相当します。高帯域幅データの場合、RAMが不足しないようにここでより低い値を使用することをほぼ確実にお勧めします。

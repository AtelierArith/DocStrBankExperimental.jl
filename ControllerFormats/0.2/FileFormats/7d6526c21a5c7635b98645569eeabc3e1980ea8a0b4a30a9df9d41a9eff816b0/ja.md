```
write_Sherlock(N::FeedforwardNetwork, filename::String)
```

[Sherlock](https://github.com/souradeep-111/sherlock/blob/bf34fb4713e5140b893c98382055fb963230d69d/sherlock-network-format.pdf)形式でファイルにニューラルネットワークを書き込みます。

### 入力

  * `N`        – フィードフォワードニューラルネットワーク
  * `filename` – 出力ファイルの名前

### 出力

`nothing`。ネットワークは出力ファイルに書き込まれます。

### 注意事項

Sherlock形式では、すべての活性化関数がReLUである必要があります。 ```

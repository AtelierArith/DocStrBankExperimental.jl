```
read_Sherlock(filename::String)
```

[Sherlock](https://github.com/souradeep-111/sherlock/blob/bf34fb4713e5140b893c98382055fb963230d69d/sherlock-network-format.pdf)形式で保存されたニューラルネットワークを読み込みます。

### 入力

  * `filename` – Sherlockファイルの名前

### 出力

[`FeedforwardNetwork`](@ref)。

### 注意事項

すべての層は出力層を含めて、暗黙的にReLU活性化関数を使用します。

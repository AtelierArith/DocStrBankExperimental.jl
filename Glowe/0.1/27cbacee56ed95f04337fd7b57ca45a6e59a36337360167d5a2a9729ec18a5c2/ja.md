```
shuffle(cooccurences, shuffled; verbose=2, memory=4.0, array_size=nothing, temp_file="temp_shuffle")
```

単語-単語の共起ファイルのエントリをシャッフルします。

# 引数

  * `cooccurences::AbstractString` 入力共起ファイルのパス
  * `shuffled::AbstractString` 出力シャッフルされた共起ファイルのパス

# キーワード引数

  * `verbose::Int` 冗長性を設定します: 0, 1, または 2 (デフォルト)
  * `memory::Float64` メモリ消費のソフトリミット、GB単位; デフォルトは 4.0
  * `array_size::Union{Nothing, Int}` ディスクに書き込む前にシャッフルするデータのチャンクを格納するバッファの長さ <int> の制限。この値は `memory` によって自動的に生成される値を上書きします
  * `temp_file`::String 一時ファイルの拡張子を除いたファイル名; デフォルトは "temp_shuffle"

# 例

```
# cooccurences.bin が存在し、`cooccur` によって作成されたと仮定します
julia> shuffle("cooccurences.bin", "shuffled.bin", verbose=2, memory=8.0)
```

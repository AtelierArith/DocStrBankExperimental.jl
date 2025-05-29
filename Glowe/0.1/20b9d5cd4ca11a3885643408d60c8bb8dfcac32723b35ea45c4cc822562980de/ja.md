```
cooccur(corpus, vocab, cooccurrences; verbose=2, symmetric=0, window_size=15, memory=4.0, max_product=nothing, overflow_length=nothing, overflow_file="overflow", distance_weighting=1)
```

単語間の共起統計を計算します。

# 引数

  * `corpus::AbstractString` 入力コーパスファイルのパス
  * `vocab::AbstractString` 入力語彙ファイルのパス（語彙は `vocab_count` によって生成された切り捨てられたユニグラムカウントを含みます）
  * `cooccurrences::AbstractString` 出力共起ファイルのパス

# キーワード引数

  * `verbose::Int` 冗長性を設定します: 0, 1, 2（デフォルト）または 3
  * `symmetric::Int` <int> = 0 の場合、左コンテキストのみを使用します; <int> = 1（デフォルト）の場合、左と右の両方を使用します
  * `window_size::Int` 左側のコンテキスト単語の数（および symmetric = 1 の場合は右側も）; デフォルトは 15
  * `memory::Float64` メモリ消費のソフトリミット、GB単位 – 簡単なヒューリスティックに基づいているため、非常に正確ではありません; デフォルトは 4.0
  * `max_product::Union{Nothing, Int}` 2つの共起する単語の頻度カウントの最大積<int>を指定することによって、密な共起配列のサイズを制限します。この値は `memory` によって自動的に生成される値を上書きします。通常は非常に大きなコーパスで使用するためにのみ調整が必要です
  * `overflow_length::Union{Nothing, Int}` 密な配列に収まらない共起データをディスクに書き込む前にバッファリングするスパースオーバーフロー配列の長さ<int>を制限します。この値は `memory` によって自動的に生成される値を上書きします。通常は非常に大きなコーパスで使用するためにのみ調整が必要です
  * `overflow_file::String` 一時ファイルの拡張子を除くファイル名; デフォルトは "overflow"
  * `distance_weighting::Int` <int> = 0 の場合、単語間の距離によって共起カウントを重み付けしません; <int> = 1（デフォルト）の場合、単語間の距離の逆数によって共起カウントを重み付けします

# 例

```
# vocab.txt が存在し、`vocab_count` によって作成されたと仮定します
julia> cooccur("corpus.txt", "vocab.txt", "cooccurrences.bin", verbose=2, symmetric=0, window_size=10, memory=8.0, overflow_file="tempoverflow")
```

```
vocab_count(corpus, vocab; max_vocab=100_000, min_count=10, verbose=2)
```

ユニグラムカウントを抽出します。

# 引数

  * `corpus::AbstractString` 入力コーパスファイルのパス
  * `vocab::AbstractString` 出力語彙ファイルのパス

# キーワード引数

  * `verbose::Int` 冗長性を設定します: 0, 1 または 2 (デフォルト)
  * `max_vocab::Int` 語彙サイズの上限、すなわち最も頻繁に出現する<int>の単語を保持します。最小頻度の単語は、アルファベット全体に均等に分布するようにランダムにサンプリングされます。
  * `min_count::Int` <int>回未満出現する単語は破棄されるという下限。

# 例

```
julia> vocab_count("corpus.txt", "vocab.txt", verbose=2, max_vocab=100_000, min_count=10)
```

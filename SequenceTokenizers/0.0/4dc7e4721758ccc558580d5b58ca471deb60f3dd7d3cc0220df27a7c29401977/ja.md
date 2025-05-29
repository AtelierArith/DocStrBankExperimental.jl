```
SequenceTokenizers
```

シンボルのシーケンスを数値インデックスにトークン化し、その逆を行うためのモジュールです。このモジュールは、トークナイザーの作成、シーケンスのエンコーディング、およびトークン化されたデータのワンホット表現を扱うための機能を提供します。

# エクスポート

  * `SequenceTokenizer`: シーケンスをトークン化するための構造体
  * `onehot_batch`: トークン化されたシーケンスをワンホット表現に変換
  * `onecold_batch`: ワンホット表現をトークン化されたシーケンスに戻す

# 例

```julia
using SequenceTokenizers

# DNAシーケンス用のトークナイザーを作成
dna_alphabet = ['A', 'C', 'G', 'T']
tokenizer = SequenceTokenizer(dna_alphabet, 'N')

# シーケンスをトークン化
seq = "ACGTACGT"
tokenized = tokenizer(seq)

# ワンホット表現に変換
onehot = onehot_batch(tokenizer, tokenized)

# トークンに戻す
recovered = onecold_batch(tokenizer, onehot)
```

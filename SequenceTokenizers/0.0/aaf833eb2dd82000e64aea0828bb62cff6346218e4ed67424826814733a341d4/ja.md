```
SequenceTokenizer{T, V <: AbstractVector{T}}
```

シンボルのシーケンスを数値インデックスにトークン化するための構造体です。

# フィールド

  * `alphabet::V`: シーケンス内の有効なシンボルのセット
  * `lookup::Vector{UInt32}`: シンボルからインデックスへの高速変換のためのルックアップテーブル
  * `unksym::T`: 不明なトークンに使用するシンボル
  * `unkidx::UInt32`: 不明なシンボルに割り当てられたインデックス

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
```

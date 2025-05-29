```
(tokenizer::SequenceTokenizer{T})(token::T) where T
```

単一のトークンを対応するインデックスに変換します。

# 引数

  * `token::T`: インデックスに変換される単一のトークン

# 戻り値

トークンのトークナイザーのアルファベット内のインデックス、または見つからない場合は未知のトークンインデックス

# 例

```julia
alphabet = ['a', 'b', 'c']
tokenizer = SequenceTokenizer(alphabet, 'x')
println(tokenizer('a'))  # 出力: 2
println(tokenizer('x'))  # 出力: 1
println(tokenizer('z'))  # 出力: 1 (未知のトークン)
```

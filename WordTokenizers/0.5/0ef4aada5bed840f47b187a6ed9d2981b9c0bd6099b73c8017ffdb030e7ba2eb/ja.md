```
improved_penn_tokenize(input::AbstractString)
```

改善されたペンツリー銀行トークナイザー。これはNLTKの修正されたペン・トークナイザーのポートです。実際にはどこにも文書化されていないと思われるいくつかの小さな変更が含まれています。しかし、`cannot cannot`のようなものは`can not can not`に変わり、元のものは`can not cannot`を生成します。

トークナイザーは依然として収縮形を分離します：「shouldn't」は["should", "n't"]になります。

入力は単一の文であるべきですが、再度言いますが、そうでなくても比較的問題ないでしょう。あなたがそれを何のために使いたいかによります。

これはNLTKの`nltk.tokenize.TreeBankWordTokenizer.tokenize`に一致します。

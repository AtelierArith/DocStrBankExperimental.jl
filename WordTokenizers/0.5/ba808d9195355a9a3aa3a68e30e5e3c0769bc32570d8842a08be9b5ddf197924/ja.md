```
nltk_word_tokenize(input)
```

NLTKの単語トークナイザーです。主にユニコードをより適切に処理するために、句読点を保持するペンツリーバンクトークナイザーの拡張です。

句読点は依然として独自のトークンとして保持されます。これには、単語から削除されるピリオドが含まれます。

トークナイザーは依然として収縮形を分離します：「shouldn't」は["should", "n't"]になります。

入力は単一の文であるべきですが、そうでなくても比較的問題ないでしょう。正確に何のために使用するかによります。

これは、文のトークナイジングステップを除いた、最も一般的に使用される`nltk.word_tokenize`に一致します。

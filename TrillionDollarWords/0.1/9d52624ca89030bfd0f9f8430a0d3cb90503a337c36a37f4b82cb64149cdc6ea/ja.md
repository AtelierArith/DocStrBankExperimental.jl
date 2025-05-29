```
layerwise_activations(mod::BaselineModel, queries::DataFrame)
```

与えられたクエリに対してモデルのフォワードパスを計算し、`sentence_id`によって一意に識別される層ごとの活性化を`DataFrame`で返します。`load_model`に`output_hidden_states=false`が渡された場合（デフォルト）、最後の層のみが返されます。`load_model`に`output_hidden_states=true`が渡された場合、すべての層が返されます。`layer`列は層の番号を示します。

各単一の活性化は独自のセルを受け取り、出力をCSVファイルに保存できるようにします。

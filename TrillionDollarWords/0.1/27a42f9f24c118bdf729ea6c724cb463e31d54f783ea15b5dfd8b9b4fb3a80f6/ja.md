```
laywerwise_activations(mod::BaselineModel, queries::Vector{String})
```

与えられたクエリに対してモデルのフォワードパスを計算し、`HGFRobertaModel`のレイヤーごとのアクティベーションを返します。`load_model`に`output_hidden_states=false`が渡された場合（デフォルト）、最後のレイヤーのみが返されます。`load_model`に`output_hidden_states=true`が渡された場合、すべてのレイヤーが返されます。分類用のヘッドでモデルがロードされている場合、最終的な線形レイヤーに入るアクティベーションが返されます。

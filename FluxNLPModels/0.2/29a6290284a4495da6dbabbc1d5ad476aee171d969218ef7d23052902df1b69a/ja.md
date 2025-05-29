```
minibatch_next_train!(nlp::AbstractFluxNLPModel)
```

`nlp.training_minibatch_iterator` から次のミニバッチを選択します。イテレータ `nlp.current_training_minibatch` の新しい現在の状態を返します。 `minibatch_next_train!` はループまたはメソッド呼び出しで使用されることを目的としています。falseを返す場合、それはミニバッチの終わりに達したことを意味します。

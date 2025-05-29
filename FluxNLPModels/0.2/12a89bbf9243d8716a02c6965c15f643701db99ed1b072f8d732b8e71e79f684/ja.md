```
minibatch_next_test!(nlp::AbstractFluxNLPModel)
```

`nlp.test_minibatch_iterator` から次のミニバッチを選択します。イテレータ `nlp.current_test_minibatch` の新しい現在の状態を返します。 `minibatch_next_test!` はループまたはメソッド呼び出しで使用されることを目的としています。falseを返す場合、それはミニバッチの終わりに達したことを意味します。

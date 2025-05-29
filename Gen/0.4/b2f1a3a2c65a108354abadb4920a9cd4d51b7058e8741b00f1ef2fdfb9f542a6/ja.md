```
req::Bool = accepts_output_grad(gen_fn::GenerativeFunction)
```

戻り値が任意のトレースに対する*勾配ソース要素*に依存しているかどうかを示すブール値を返します。

勾配ソース要素は次のとおりです：

  * `has_argument_grads`で位置がtrueの任意の引数
  * 任意の学習可能なパラメータ
  * `choice_gradients`によって選択可能なアドレスで行われたランダムな選択

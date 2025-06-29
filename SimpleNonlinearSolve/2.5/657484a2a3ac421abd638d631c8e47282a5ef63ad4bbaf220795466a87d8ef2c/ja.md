```
SimpleNewtonRaphson(autodiff)
SimpleNewtonRaphson(; autodiff = nothing)
```

低オーバーヘッドのニュートン-ラフソン法の実装です。このメソッドは、スカラーおよび静的配列の問題に対してメモリを割り当てません。

!!! note
    オーバーヘッドを減らすために、このメソッドは他のメソッドの高レベルのエラーハンドリングの一部を省略しています。したがって、より良いエラーメッセージを確認するには、`NewtonRaphson`のような他のメソッドを使用してください。


### キーワード引数

  * `autodiff`: ヤコビ行列に使用されるバックエンドを決定します。デフォルトは `nothing`（すなわち、自動バックエンド選択）です。有効な選択肢には、`DifferentiationInterface.jl`のヤコビ行列バックエンドが含まれます。

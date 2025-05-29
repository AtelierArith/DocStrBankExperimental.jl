```
SimpleHalley(autodiff)
SimpleHalley(; autodiff = nothing)
```

ハレー法の低オーバーヘッド実装です。

!!! note
    オーバーヘッドを減らす一環として、このメソッドは他のメソッドの高レベルのエラーキャッチを一部省略しています。したがって、より良いエラーメッセージを確認するには、`NewtonRaphson`のような他のメソッドを使用してください。


### キーワード引数

  * `autodiff`: ヤコビ行列に使用されるバックエンドを決定します。デフォルトは `nothing`（すなわち、自動バックエンド選択）です。有効な選択肢には、`DifferentiationInterface.jl`のヤコビ行列バックエンドが含まれます。

イート積分を詳細に説明する構造体です。これは、被積分関数を詳細に説明するUnivariateFunctionと、積分のプロセスのIDを詳細に説明するシンボルを含んでいます。

通常の（および最も一般的な）コンストラクタは次のとおりです：

```
ItoIntegral(brownian_id_::Symbol, f_::UnivariateFunction)
```

被積分関数が平坦な関数である`ItoIntegral`のための便利なコンストラクタは次のとおりです：

```
ItoIntegral(brownian_id_::Symbol, variance_::Real)
```

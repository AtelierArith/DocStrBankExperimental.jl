```
SimpleChain([inputdim::Union{Integer,Tuple{Vararg{Integer}}, ] layers)
```

`SimpleChain`を構築します。オプションの`inputdim`引数により、`SimpleChains`は入力のサイズをチェックできます。これを`static`にすることで、`SimpleChains`はコンパイル時にサイズとループ境界を推論できます。バッチサイズは一般的に`inputdim`に含めるべきではありません。`inputdim`が指定されていない場合、`init_params`などのいくつかのメソッドは、入力サイズの関数である可能性があるため、サイズを追加の引数として渡す必要があります（例：`TurboDense`レイヤーの場合）。

`layers`引数は、さまざまな`SimpleChains`レイヤー（例：`TurboDense`、`Conv`、`Activation`、`Flatten`、`Dropout`、または`MaxPool`）を保持します。オプションで`AbstractLoss`レイヤーで終了することもできます。

これらのオブジェクトは呼び出し可能です。例えば、

```julia
c = SimpleChain(...);
p = SimpleChains.init_params(c);
c(X, p) # Xは独立変数で、`p`はパラメータベクトルです。
```

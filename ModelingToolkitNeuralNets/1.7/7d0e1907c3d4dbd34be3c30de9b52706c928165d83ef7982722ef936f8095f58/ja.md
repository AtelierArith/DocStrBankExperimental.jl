```
SymbolicNeuralNetwork(; n_input = 1, n_output = 1,
    chain = multi_layer_feed_forward(n_input, n_output),
    rng = Xoshiro(0),
    init_params = Lux.initialparameters(rng, chain),
    nn_name =  :NN,
    nn_p_name = :p,
    eltype = Float64)
```

ニューラルネットワークのためのシンボリックパラメータとそのパラメータのためのものを作成します。例:

```
chain = multi_layer_feed_forward(2, 2)
NN, p = SymbolicNeuralNetwork(; chain, n_input=2, n_output=2, rng = StableRNG(42))
```

NNとpは、後でシステムの一部として使用できるシンボリックパラメータです。シンボリック変数の名前を変更するには、`nn_name`と`nn_p_name`を使用します。ニューラルネットワークの予測を得るには、次のようにします。

```
pred ~ NN(input, p)
```

ここで、`pred`と`input`はそれぞれ長さ`n_output`と`n_input`のシンボリックベクトル変数です。

これを方程式の外で使用するには、シンボルのデフォルト値を取得し、同様の呼び出しを行うことができます。

```
defaults(sys)[sys.NN](input, nn_p)
```

ここで、`sys`は`NN`を含むシステム（例: `ODESystem`）であり、`input`は長さ`n_input`のベクトルで、`nn_p`はニューラルネットワークのパラメータ値を表すベクトルです。

基礎となるLuxモデルを取得するには、`get_network(defaults(sys)[sys.NN])`を使用するか、

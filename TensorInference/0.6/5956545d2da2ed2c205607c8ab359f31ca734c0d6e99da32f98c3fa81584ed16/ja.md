```julia
sample(
    tn::TensorInference.TensorNetworkModel,
    n::Int64;
    usecuda,
    queryvars
) -> TensorInference.Samples{Int64}

```

テンソルネットワークに基づく確率モデルからサンプルを生成します。返されるのはベクトルのベクトルで、各要素は `get_vars(tn)` で定義された構成です。

### 引数

  * `tn` はテンソルネットワークモデルです。
  * `n` は返されるサンプルの数です。

### キーワード引数

  * `usecuda` はテンソル計算にCUDAを使用するかどうかを示すブールフラグです。
  * `queryvars` はサンプリングされる変数で、デフォルトは `get_vars(tn)` です。

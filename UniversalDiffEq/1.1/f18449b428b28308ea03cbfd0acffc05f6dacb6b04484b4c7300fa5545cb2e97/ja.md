```
BayesianUDE
```

ベイズUDEおよびNODEモデルのモデル構造、パラメータ、およびデータに使用される基本データ構造。 ...

# 要素

  * times: 各観測のための時間のベクトル
  * data: 各時間点での観測の行列
  * X: モデルによって使用される任意の共変量を含むDataFrame
  * data_frame: 各観測の時間と状態変数の値の列を持つDataFrame
  * parameters: モデルパラメータを格納するComponentArray
  * loss_function: モデルをフィットさせるために使用される損失関数
  * process_model: モデル予測を定義するために使用されるJuliaの可変構造体
  * process_loss: モデル予測のパフォーマンスを測定するために使用されるJuliaの可変構造体
  * observation_model: 状態変数の推定値に基づいて観測を予測するために使用されるJuliaの可変構造体
  * observation_loss: 観測モデルのパフォーマンスを測定するために使用されるJuliaの可変構造体
  * process_regularization: プロセスモデルの正則化に必要なデータを格納するために使用されるJuliaの可変構造体
  * observation_regularization: 観測モデルの正則化に必要なデータを格納するために使用されるJuliaの可変構造体
  * constructor: 同一の構造を持つUDEモデルを初期化する関数。

...

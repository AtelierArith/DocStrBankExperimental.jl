```julia
sci_train!(ann, data; ...)
sci_train!(ann, data, opt; device, epoch, batch)

```

科学的機械学習トレーナー

# 引数

  * $$
    ann
    $$

    : ニューラルネットワークモデル
  * $$
    data
    $$

    : データセットのタプル (X, Y)
  * $$
    opt
    $$

    : オプティマイザ
  * $$
    epoch
    $$

    : エポック数
  * $$
    batch
    $$

    : バッチサイズ
  * $$
    device
    $$

    : cpu / gpu

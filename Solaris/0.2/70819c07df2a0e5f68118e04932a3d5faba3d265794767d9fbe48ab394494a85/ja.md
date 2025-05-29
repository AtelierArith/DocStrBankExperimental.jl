```julia
sci_train(ann, data; ...)
sci_train(ann, data, θ; ...)
sci_train(
    ann,
    data,
    θ,
    opt,
    args;
    device,
    iters,
    ad,
    batch,
    shuffle,
    kwargs...
)

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

    : データセット
  * $$
    θ
    $$

    : ニューラルネットワークのパラメータ
  * $$
    opt
    $$

    : オプティマイザ
  * $$
    args
    $$

    : その他の引数
  * $$
    device
    $$

    : cpu / gpu
  * $$
    iters
    $$

    : 最大反復回数
  * $$
    ad
    $$

    : 自動微分の種類
  * $$
    batch
    $$

    : バッチサイズ
  * $$
    shuffle
    $$

    : データをシャッフルする（true）かしない（false）
  * $$
    kwargs
    $$

    : その他のキーワード引数

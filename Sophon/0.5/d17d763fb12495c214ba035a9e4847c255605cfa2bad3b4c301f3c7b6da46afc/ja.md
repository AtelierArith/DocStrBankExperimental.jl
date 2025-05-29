```
FactorizedDense(in_dims::Int, out_dims::Int, activation=identity;
                     mean::AbstractFloat=1.0f0, std::AbstractFloat=0.1f0,
                     init_weight=kaiming_uniform(activation), init_bias=zeros32)
```

重みが2つの部分に因数分解された`Dense`レイヤーを作成します。各行のスケーリング係数と重み行列です。

## 引数

  * `in_dims`: 入力次元の数
  * `out_dims`: 出力次元の数
  * `activation`: 活性化関数

## キーワード引数

  * `mean`: スケーリング係数の平均
  * `std`: スケーリング係数の標準偏差
  * `init_weight`: 重み初期化関数
  * `init_bias`: バイアス初期化関数

## 入力

  * `x`: 入力ベクトルまたは行列

## 戻り値

  * `y = activation.(scale * weight * x + bias)`。
  * 空の`NamedTuple()`。

## パラメータ

  * `scale`: スケーリング係数。形状: `(out_dims, 1)`
  * `weight`: サイズ`(out_dims, in_dims)`の重み行列。
  * `bias`: サイズ`(out_dims, 1)`のバイアス。

## 参考文献

[wang2022random](@cite)

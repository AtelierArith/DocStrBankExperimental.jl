```
GroupNorm(chs::Integer, groups::Integer, activation=identity; init_bias=zeros32,
          init_scale=ones32, affine=true, epsilon=1f-5)
```

[グループ正規化](https://arxiv.org/abs/1803.08494) レイヤー。

## 引数

  * `chs`: データのチャネル次元のサイズ。`N` 次元の配列が与えられた場合、`N-1` 番目をチャネル次元と呼びます。特徴ベクトルのバッチの場合、これは単にデータ次元であり、`WHCN` 画像の場合は通常のチャネル次元です。
  * `groups` は、統計が計算されるグループの数です。チャネルの数はグループの数の整数倍でなければなりません。
  * `activation`: 正規化の後、要素ごとの活性化 `activation` が適用されます。

## キーワード引数

  * `epsilon`: 数値的安定性のために分母に追加される値
  * `affine=true` の場合、学習可能なチャネルごとのバイアスとスケールパラメータを通じて、入力にシフトと再スケールも適用されます。

      * `init_bias`: `bias` の初期化方法を制御します
      * `init_scale`: `scale` の初期化方法を制御します

# 拡張ヘルプ

## 入力

  * `x`: `size(x, N - 1) = chs` かつ `ndims(x) > 2` の配列

## 戻り値

  * `y`: 正規化された配列
  * モデルの状態を更新

## パラメータ

  * `affine=true`

      * `bias`: 形状 `(chs,)` のバイアス
      * `scale`: 形状 `(chs,)` のスケール
  * `affine=false` - 空の `NamedTuple()`

## 状態

  * `training`: トレーニング/推論モードを確認するために使用されます

推論中は `Lux.testmode` を使用してください。

## 例

```jldoctest
julia> Chain(Dense(784 => 64), GroupNorm(64, 4, relu), Dense(64 => 10), GroupNorm(10, 5))
Chain(
    layer_1 = Dense(784 => 64),         # 50_240 パラメータ
    layer_2 = GroupNorm(64, 4, relu, affine=true),  # 128 パラメータ
    layer_3 = Dense(64 => 10),          # 650 パラメータ
    layer_4 = GroupNorm(10, 5, affine=true),  # 20 パラメータ
)         # 合計: 51_038 パラメータ、
          #        さらに 0 状態。
```

他にも [`GroupNorm`](@ref)、[`InstanceNorm`](@ref)、[`LayerNorm`](@ref)、[`WeightNorm`](@ref) を参照してください。

```
RotaryPositionalEmbedding(
    dim::IntegerType; max_sequence_length::IntegerType=4096, base::IntegerType=10000
)
```

ロタリーポジショナルエンコーディング。詳細は [su2024roformer](@citet) を参照してください。

従来の実装は特徴次元内の連続する要素のペアを回転させますが、デフォルトの実装は効率のために特徴次元の半分のストライドでペアを回転させます。

## 引数

  * `dim`: 回転させる特徴次元。入力特徴がdimsより大きい場合、残りは変更されません。

## キーワード引数

  * `base`: ポジショナルエンコーディングの各次元の角周波数を計算するために使用される基数。デフォルト: `10000`。
  * `max_sequence_length`: 最大シーケンス長。デフォルト: `4096`。

## 入力

  * 4D AbstractArray s.t.

      * size(x, 1) == dim
      * size(x, 3) ≤ max*sequence*length

## 戻り値

  * 入力と同じサイズの4D AbstractArray。

## 状態

  * `cos_cache` と `sin_cache` を含む NamedTuple。

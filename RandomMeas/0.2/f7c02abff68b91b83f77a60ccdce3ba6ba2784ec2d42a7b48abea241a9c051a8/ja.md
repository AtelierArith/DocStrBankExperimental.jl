```
trace(shadows::AbstractArray{<:AbstractShadow})
```

シャドウオブジェクトのコレクションに対してトレースを計算します。

# 引数:

  * `shadows::AbstractArray{<:AbstractShadow}`: シャドウオブジェクトのコレクション（ベクトル、行列など）。

# 戻り値

入力と同じ次元を持つ各シャドウに対応するスカラーのトレース値の配列。

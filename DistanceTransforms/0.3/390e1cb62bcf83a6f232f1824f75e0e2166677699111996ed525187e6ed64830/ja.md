## `transform`

```julia
transform(f::AbstractVector)
transform(img::AbstractMatrix; threaded=true)
transform(vol::AbstractArray{<:Real,3}; threaded=true)
transform(img::AbstractGPUMatrix)
```

新しい配列を返す非インプレースの二乗ユークリッド距離変換。必要な中間配列を内部で割り当てます。

  * 最初の関数はベクトルに対して動作します。
  * 2番目の関数はオプションのスレッド処理を伴う行列に対して動作します。
  * 3番目の関数はオプションのスレッド処理を伴う3D配列に対して動作します。
  * 4番目の関数はGPU行列に特化しています。

`threaded`パラメータは、CPU上での並列計算を有効または無効にするために使用できます。

#### 引数

  * `f/img/vol`: 変換される入力ベクトル、行列、または3D配列。

#### 例

```julia
f = rand([0f0, 1f0], 10)
f_bool = boolean_indicator(f)
f_tfm = transform(f_bool)
```

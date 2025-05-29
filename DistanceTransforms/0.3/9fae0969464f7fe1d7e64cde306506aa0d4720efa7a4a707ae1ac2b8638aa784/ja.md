## `transform!`

```julia
transform!(f::AbstractVector, output, v, z)
transform!(img::AbstractMatrix, output, v, z; threaded=true)
transform!(vol::AbstractArray{<:Real,3}, output, v, z, temp; threaded=true)
transform!(img::AbstractGPUMatrix, output, v, z)
```

インプレースの二乗ユークリッド距離変換。これらの関数は入力データに変換を適用し、結果を`output`引数に格納します。

  * 最初の関数はベクトルに対して動作します。
  * 2番目の関数はオプションのスレッド処理を伴う行列に対して動作します。
  * 3番目の関数はオプションのスレッド処理を伴う3D配列に対して動作します。
  * 4番目の関数はGPU行列に特化しています。

中間配列`v`と`z`（および3D配列の場合の`temp`）は計算に使用されます。`threaded`パラメータはCPU上での並列計算を有効にします。

#### 引数

  * `f`: 入力ベクトル、行列、または3D配列。
  * `output`: 結果を格納するための事前割り当てされた配列。
  * `v`: `f`の次元に一致するインデックス用の事前割り当てされた配列。
  * `z`: `f`よりも1要素大きい中間値用の事前割り当てされた配列。
  * `temp`: 3D配列を変換する際の中間値用の事前割り当てされた配列で、`output`の次元に一致します。

#### 例

```julia
f = rand([0f0, 1f0], 10)
f_bool = boolean_indicator(f)
output = similar(f)
v = ones(Int32, size(f))
z = ones(eltype(f), size(f) .+ 1)
transform!(f_bool, output, v, z)
```

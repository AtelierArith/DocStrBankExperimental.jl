```
mcpc3ds(phase, mag; TEs, keyargs...)

mcpc3ds(compl; TEs, keyargs...)

mcpc3ds(phase; TEs, keyargs...)
```

4D（マルチエコー）および5D（マルチエコー、未結合）入力に対してMCPC-3D-Sコイル結合と位相オフセット除去を実行します。

## オプションのキーワード引数

  * `echoes`: 定義されたエコーのみを使用します。デフォルト: `echoes=[1,2]`
  * `sigma`: 位相オフセットのスムージングパラメータ。デフォルト: `sigma=[10,10,5]`
  * `bipolar_correction`: 線形位相アーチファクトを除去します。デフォルト: `bipolar_correction=false`
  * `po`: 位相オフセットはこの配列に保存されます。位相オフセットを取得したり、メモリマッピングで作業するために使用できます。

# 例

```julia-repl
julia> phase = readphase("phase5D.nii")
julia> mag = readmag("mag5D.nii")
julia> combined = mcpc3ds(phase, mag; TEs=[4,8,12])
```

メモリに収まらない非常に大きなファイルの場合、未結合データはディスクにメモリマップして処理できます：

```julia-repl
julia> phase = readphase("phase5D.nii"; mmap=true)
julia> mag = readmag("mag5D.nii"; mmap=true)
julia> po_size = (size(phase)[1:3]..., size(phase,5))
julia> po = write_emptynii(po_size, "po.nii")
julia> combined = mcpc3ds(phase, mag; TEs=[4,8,12], po)
```

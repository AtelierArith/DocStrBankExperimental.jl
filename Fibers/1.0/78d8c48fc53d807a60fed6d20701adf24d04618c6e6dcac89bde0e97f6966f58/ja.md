```
mri_write(mri::MRI, outfile::String, datatype::DataType=Float32)
```

ディスクにMRIボリュームを書き込みます。エラーが発生した場合（つまり、書き込まれたバイト数がボリュームのサイズに基づいて期待されるものと異なる場合）、trueを返します。

# 引数

  * `mri::MRI`: `mri_read()`によって返されるような構造体。ジオメトリ（すなわち、方向コサイン、ボクセル解像度、P0）はすべてmri.vox2ras0から再計算されます。したがって、メソッドが他のフィールドの1つを変更した場合、例えばmri.x_r、この変更は出力ボリュームには反映されません。
  * `outfile::String`: 出力ファイルへのパスで、次のいずれかになります：

    1. MGHファイル、例：f.mghまたはf.mgz（非圧縮または圧縮）
    2. NIfTIファイル、例：f.niiまたはf.nii.gz（非圧縮または圧縮）。
  * `datatype::DataType=eltype(mri.vol)`: NIfTIにのみ適用され、UInt8、Int16、Int32、Float32、Float64、Int8、UInt16、UInt32のいずれかです。デフォルトでは、ボリューム配列のネイティブデータ型はディスクに書き込む際に保持されます。

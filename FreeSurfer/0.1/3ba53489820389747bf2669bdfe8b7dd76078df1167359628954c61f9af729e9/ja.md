```
mri_write(mri::MRI, outfile::String, datatype::DataType=Float32)
```

MRIボリュームをディスクに書き込みます。エラーが発生した場合はtrueを返します（すなわち、書き込まれたバイト数がボリュームのサイズに基づいて期待されるものと異なる場合）。

# 引数

  * `mri::MRI`: `mri_read()`によって返されるような構造体。ジオメトリ（すなわち、方向コサイン、ボクセル解像度、P0）はすべてmri.vox2ras0から再計算されます。したがって、メソッドが他のフィールドの1つを変更した場合、例えばmri.x_r、これらの変更は出力ボリュームには反映されません。
  * `outfile::String`: 出力ファイルへのパスで、次のいずれかになります：

    1. MGHファイル、例：f.mghまたはf.mgz（非圧縮または圧縮）
    2. NIfTIファイル、例：f.niiまたはf.nii.gz（非圧縮または圧縮）。
  * `datatype::DataType=Float32`: NIfTIにのみ適用され、UInt8、Int16、Int32、Float32、Float64、Int8、UInt16、UInt32のいずれかです。

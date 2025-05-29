```
mri_read(infile::String, headeronly::Bool=false, permuteflag::Bool=false)
```

ディスクから画像ボリュームを読み込み、mri.hで定義されたFreeSurfer MRI構造体に似た`MRI`構造体を返します。

# 引数

  * `infile::String`: 入力のパスで、次のいずれかです：

    1. MGHファイル、例：f.mghまたはf.mgz
    2. NIfTIファイル、例：f.niiまたはf.nii.gz
    3. ファイルステムの場合、その形式と完全なファイル名は、ディスク上にある`infile`.{mgh, mgz, nii, nii.gz}という名前のファイルを見つけることによって決定されます。
    4. Brukerスキャンディレクトリで、次のファイルが含まれていることが期待されます：method、pdata/1/reco、pdata/1/2dseq
  * `headeronly::Bool=false`: trueの場合、ピクセルデータは読み込まれません。
  * `permuteflag::Bool==false`: trueの場合、画像ボリュームの最初の2次元が出力構造体の.vol、.volsize、および.volresフィールドで置換されます（これはMATLABバージョンのデフォルトの動作です）。`permuteflag`は、常に（列、行、スライス）規則でインデックスをマッピングするvox2ras行列には影響しません。

# 出力

`MRI`構造体内：

  * 時間はms単位で、角度はラジアン単位です。
  * `vox2ras0`: このフィールドには、0ベースの（列、行、スライス）ボクセルインデックスを（x、y、z）座標に変換するvox2ras行列が含まれています。これは、mri_write()がすべてのジオメトリ情報（例：方向コサイン、ボクセル解像度、P0）を導出するために使用する行列でもあります。したがって、構造体の他のジオメトリフィールドが変更されると、その変更は出力ボリュームに反映されません。
  * `vox2ras1`: このフィールドには、1ベースの（列、行、スライス）ボクセルインデックスを（x、y、z）座標に変換するvox2ras行列が含まれています。
  * `niftihdr`: 入力ファイルがNIfTIの場合、このフィールドには`NIfTIheader`構造体が含まれています。

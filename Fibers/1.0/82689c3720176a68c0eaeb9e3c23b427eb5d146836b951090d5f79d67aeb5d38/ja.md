```
mri_read(infile::String; headeronly::Bool=false, permutedata::Bool=false, reco::Integer=1)
```

ディスクから画像ボリュームを読み込み、mri.hで定義されたFreeSurfer MRI構造体に似た`MRI`構造体を返します。

# 引数

  * `infile::String`: 入力のパスで、次のいずれかです：

    1. MGHファイル、例：f.mghまたはf.mgz
    2. NIfTIファイル、例：f.niiまたはf.nii.gz
    3. ファイルステムの場合、その形式と完全なファイル名は、ディスク上にある`infile`.{mgh, mgz, nii, nii.gz}という名前のファイルを見つけることによって決定されます。
    4. Brukerスキャンディレクトリで、次のファイルが含まれていることが期待されます：method、acqp、pdata/1/reco、pdata/1/2dseq

# オプション引数

  * `headeronly::Bool=false`: trueの場合、ピクセルデータは読み込まれません。
  * `permutedata::Bool==false`: trueの場合、画像ボリュームの最初の2次元は出力構造の.vol、.volsize、および.volresフィールドで置換されます（これはMATLABバージョンのデフォルトの動作です）。`permutedata`は、常に（列、行、スライス）規則でインデックスをマッピングするvox2ras行列には影響しません。
  * `reco::Integer=1`: （Brukerスキャンディレクトリの読み込みにのみ関連）読み込む画像再構成の数で、1はオンライン再構成を示し、高い数は取得後に行われた追加のオフライン再構成を示します。

# 出力

`MRI`構造体内：

  * 時間はms単位で、角度はラジアン単位です。
  * `vox2ras0`: このフィールドには、0ベースの（列、行、スライス）ボクセルインデックスを（x、y、z）座標に変換するvox2ras行列が含まれています。これは、mri_write()がすべてのジオメトリ情報（例：方向コサイン、ボクセル解像度、P0）を導出するために使用する行列でもあります。したがって、構造体の他のジオメトリフィールドが変更されると、その変更は出力ボリュームに反映されません。
  * `vox2ras1`: このフィールドには、1ベースの（列、行、スライス）ボクセルインデックスを（x、y、z）座標に変換するvox2ras行列が含まれています。
  * `niftihdr`: 入力ファイルがNIfTIの場合、このフィールドには`NIfTIheader`構造体が含まれています。

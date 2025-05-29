```
coord, Data_3D_Arrays, Name_Vec = read_data_VTR(fname)
```

VTR（構造化グリッド）VTKファイル`fname`を読み込み、座標、データ配列、およびデータの名前を抽出します。一般的に、これはデータの一部のみを含んでおり、完全なデータを取得するには`*.pvtr`ファイルを開く必要があります。

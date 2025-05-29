```
tile_osm_file(filename::AbstractString, [bounds::Bounds]; nrow::Integer, ncol::Integer, [out_dir::AbstractString]
```

地図のタイル機能を提供します。`filename`は処理のために開かれ、タイルは指定された`bounds`の周りで行われます。`bounds`が指定されていない場合は、`getbounds`関数を使用して計算されます。タイルは`nrow`行と`ncol`列を持つ行列で実行されます。出力は`out_dir`というフォルダ名に書き込まれます。`out_dir`が指定されていない場合、出力は`filename`が存在する場所に書き込まれます。

作成されたファイルの名前を含むサイズ`nrow` x `ncol`の`Matrix{String}`を返します。

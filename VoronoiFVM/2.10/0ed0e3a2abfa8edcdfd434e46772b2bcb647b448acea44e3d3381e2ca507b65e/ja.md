```
TransientSolution(t0,inival;
                  in_memory=true,
                  keep_open=true,
                  fname=tempname(pwd())*".jld2"
```

初期値と初期時間を持つ過渡解のコンストラクタ。

  * `in_memory`: true（デフォルト）の場合、データはメインメモリに保持され、それ以外の場合はディスク上（JLD2を介して）
  * `keep_open`: trueの場合、オブジェクトの存在中にディスクファイルは閉じられません
  * `fname`: ディスクファイルのファイル名

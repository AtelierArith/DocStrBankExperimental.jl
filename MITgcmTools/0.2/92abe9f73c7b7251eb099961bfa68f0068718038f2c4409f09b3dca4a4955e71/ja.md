```
scan_rundir(pth::String)
```

MITgcmの実行ディレクトリと標準出力テキストファイル（"output.txt"または"STDOUT.0000"）をスキャンし、収集した情報のNamedTupleを返します（さまざまな形式）。

最初の出力は次のように見えました：`(grid=gr,packages=pac,params_time=par1,params_grid=par2,completed=co)`

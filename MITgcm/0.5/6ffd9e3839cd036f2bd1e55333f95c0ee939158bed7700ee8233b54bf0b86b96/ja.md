```
scan_rundir(config::MITgcm_config)
```

MITgcmの実行ディレクトリ（joinpath(MC,"run")）をスキャンし、見つかった場合は、標準出力テキストファイル（"output.txt"または"STDOUT.0000"）を`scan_stdout`を介してスキャンします。

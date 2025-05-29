```
fits_copy_hdu(fin::FITSFile, fout::FITSFile[, morekeys::Integer = 0])
```

入力ファイル `fin` から現在のHDUをコピーし、出力ファイル `fout` に追加します。出力ヘッダーには `morekeys` の追加キーワードのためのスペースが予約される場合があります。

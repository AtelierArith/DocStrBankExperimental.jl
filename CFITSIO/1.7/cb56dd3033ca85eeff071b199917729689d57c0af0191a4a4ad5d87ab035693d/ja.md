```
fits_copy_header(fin::FITSFile, fout::FITSFile)
```

現在のHDUに関連付けられたヘッダー（データではなく）を`fin`から`fout`にコピーします。`fout`の現在のHDUが空でない場合、それは閉じられ、新しいHDUが追加されます。ヘッダーはあるがデータはない空の出力HDUが作成されます。

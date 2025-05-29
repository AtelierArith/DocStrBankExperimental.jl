```
fits_copy_data(fin::FITSFile, fout::FITSFile)
```

現在のHDUから`fin`のデータ（ヘッダーではなく）を`fout`の現在のHDUにコピーします。これにより、出力HDU内の既存のデータが上書きされます。

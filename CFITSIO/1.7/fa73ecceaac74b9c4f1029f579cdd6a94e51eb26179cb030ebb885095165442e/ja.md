```
fits_copy_image_section(fin::FITSFile, fout::FITSFile, section::String)
```

`fin`から画像の長方形のセクションをコピーし、それを`fout`の新しいFITSプライマリ画像または画像拡張に書き込みます。セクション指定子については[`CFITSIO website`](https://heasarc.gsfc.nasa.gov/docs/software/fitsio/c/c_user/node97.html)で説明されています。

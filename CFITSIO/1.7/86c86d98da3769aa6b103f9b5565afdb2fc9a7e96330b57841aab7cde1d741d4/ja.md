```
fits_read_record(f::FITSFile, keynum::Int)::String
```

CHU内のn番目のヘッダーレコードを返します。ヘッダー内の最初のキーワードは`keynum = 1`です。

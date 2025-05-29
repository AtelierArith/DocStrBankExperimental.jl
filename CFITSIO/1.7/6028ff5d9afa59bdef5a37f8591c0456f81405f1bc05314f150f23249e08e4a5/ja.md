```
fits_read_keyn(f::FITSFile, keynum::Int) -> (name, value, comment)
```

CHU内のn番目のヘッダーレコードを返します。ヘッダー内の最初のキーワードは`keynum = 1`です。

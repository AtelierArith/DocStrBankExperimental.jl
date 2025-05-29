```
fits_hdr2str(f::FITSFile, nocomments::Bool=false)
```

CHDUのヘッダーを文字列として返します。`nocomments`が`true`の場合、コメントカードは出力から削除されます。

```
imgload(c::CifContainer, a::ImageArchive)
```

CIFブロック`c`内で最初に見つかった`_array_data.binary_id`によって参照される画像を返します。`a`は`create_archive`を使用して作成されたアーカイブです。

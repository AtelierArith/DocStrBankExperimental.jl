```
(dat, rdb_hdr) = loadpfile(fid::IOStream ; ...)
```

GE MRIスキャンPファイルから1つ以上のエコーのデータをロードします。

入力

  * `fid::IOStream`

オプション

  * `coils::AbstractVector{Int}`

これらのコイルのデータのみ取得; デフォルト: すべてのコイル

  * `echoes::AbstractVector{Int}`

これらのエコーのデータのみ取得; デフォルト: すべてのエコー

  * `slices::AbstractVector{Int}`

これらのスライスのデータのみ取得; デフォルト: `2:nslices` (注意!) 最初のスライス (dabslice=0 スロット) は破損したデータを含む可能性があります。

  * `views::AbstractVector{Int}`

これらのビューのデータのみ取得; デフォルト: すべてのビュー

  * `quiet::Bool` 非冗長性、デフォルト `false`

出力

  * `dat::Array{Complex{Int16}}` `[ndat, ncoil, nslice, necho, nview]`
  * `rdb_hdr::NamedTuple` ヘッダー情報

メモリを節約するため、出力タイプは複素数値のInt16です。

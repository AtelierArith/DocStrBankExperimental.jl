```
uncompress(zipfile::AbstractString, file::AbstractString)
```

zipファイル`zipfile`を`file`（ディレクトリ）に解凍します。この関数は、解凍されたコンテンツが`file`という名前であるかどうかを確認しません。これは、`uncompress`アクションをスキップするためのヒントとして使用されます。

ユーザーは`mv uncompress_file file`を使用して、一貫性を強制することができます。

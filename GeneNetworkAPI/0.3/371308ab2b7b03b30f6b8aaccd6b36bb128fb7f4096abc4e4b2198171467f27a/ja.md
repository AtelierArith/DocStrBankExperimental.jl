```
download_geno(group::String,format::String="geno";
                gn_url::String=gn_url(),
                path::String = "")
```

指定された`format`で`group`の遺伝子型行列をダウンロードします。

現在、`geno`形式のファイルのみで動作します。

ファイルは`path`の場所にダウンロードされます。`path`が指定されていない場合、ファイルは一時ファイルになります。

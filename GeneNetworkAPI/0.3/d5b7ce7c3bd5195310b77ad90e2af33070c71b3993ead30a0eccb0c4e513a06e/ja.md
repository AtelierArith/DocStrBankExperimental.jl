```
download_omics(dataset::String; 
                gn_url::String=gn_url(), 
                path::String = tempname())
```

指定された `dataset` のオミクス表現型をダウンロードします。ファイルは `path` の場所にダウンロードされます。`path` が指定されていない場合、ファイルは一時ファイルになります。

```
download_pheno(dataset::String;gn_url::String=gn_url())
```

指定された `dataset` の非オミクス（「臨床」）表現型をダウンロードします。ファイルは `path` の場所にダウンロードされます。`path` が指定されていない場合、ファイルは一時ファイルになります。

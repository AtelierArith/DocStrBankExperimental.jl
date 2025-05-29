```
process_file(filename[, folder]) -> FileCoverage
```

.jlファイルとその含まれるフォルダーを指定すると、ソースと一致するカバレッジファイルから対応する`FileCoverage`インスタンスを生成します。フォルダーが指定されていない場合は、ファイル名から抽出されます。

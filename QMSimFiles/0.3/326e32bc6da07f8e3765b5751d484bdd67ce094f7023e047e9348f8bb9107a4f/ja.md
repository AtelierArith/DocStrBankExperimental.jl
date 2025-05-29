```
export_qmsim_individual_blupf90(map,id,individual,snpfile; append=true)
```

個々の遺伝子型をテキストファイル `snpfile` に整数コード `id` を使用してエクスポートします。この形式はBLUPF90によってサポートされています。ファイルが存在しない場合、関数は新しいファイルを作成します。同じファイル名の `snpfile` がある場合、関数はデフォルトで既存のファイルにデータを追加します。ファイルを再作成したい場合は、この関数を呼び出す前にファイルを削除するか、`append=false` を使用してください。

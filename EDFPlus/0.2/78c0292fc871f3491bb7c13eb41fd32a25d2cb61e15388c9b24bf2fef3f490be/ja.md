```
loadfile(path::String, read_annotations=true)
```

BDF+またはEDF+タイプのファイルをロードします。パス名を受け取ります。第二引数がfalseに設定されている場合、注釈は無視されます。ヘッダーとデータを含むBEDFPlus構造体を返します。

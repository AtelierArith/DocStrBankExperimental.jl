```
append2fig(fname::String)
```

ファイル `fname` をデフォルトの名前と場所（tmp内のGMT_user.ps）に移動します。`fname` は閉じられていないPSファイルである必要があります。プロットメソッドへの後続の呼び出しは、このファイルに追加されます。共通のベースマップを使用する図を作成する際に便利で、計算が重い（遅い）場合があります。

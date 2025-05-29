```
matwrite(filename, d::Dict; compress::Bool = false, version::String)
```

変数名をキー、値を値として含む辞書をMatlabファイルに書き込み、自動的に開いて閉じます。

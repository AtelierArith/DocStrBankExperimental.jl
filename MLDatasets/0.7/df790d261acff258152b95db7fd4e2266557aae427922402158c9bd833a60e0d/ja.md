```
FileDataset([loadfn = FileIO.load,] paths)
FileDataset([loadfn = FileIO.load,] dir, pattern = "*", depth = 4)
```

ファイル `paths` のセットをデータセットとしてラップします（`paths` と同じ順序でトラバースされます）。または、`dir` を指定し、グロブ `pattern` に一致するすべてのパスを収集します（`depth` によって再帰的にグロビングします）。グロブの順序がトラバースの順序を決定します。

```
issame(file1, file2, tol=1e-4; strict=true, verbose=false) -> Bool
```

2つのVLSVファイル`file1`と`file2`が、相対許容誤差`tol`の下でほぼ同一であるかを確認します。`strict=true`の場合、ファイルサイズの違いは1%未満である必要があります。

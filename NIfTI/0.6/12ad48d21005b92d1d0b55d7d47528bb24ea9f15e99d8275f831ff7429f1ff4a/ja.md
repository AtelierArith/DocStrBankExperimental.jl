```
vox(f::NIVolume, args...,)
```

ボリューム `f` からボクセルの値を取得し、ヘッダーに指定されたスロープと切片でスケーリングします。インデックスは0ベースです。`args` はボクセルインデックスで、長さは `f` の次元数と同じである必要があります。

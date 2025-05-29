```
write_mesh(m :: TriMesh, file_name :: String; <keyword arguments>)
```

メッシュをディスクに書き込みます。

# 引数

  * `file_name :: String`: パスとファイル名を含む文字列を指定します。

# キーワード引数

  * `format :: String = "triangle"`: メッシュフォーマットを指定します。現在のオプションは `"triangle"`（Triangleのネイティブメッシュフォーマット）のみです。

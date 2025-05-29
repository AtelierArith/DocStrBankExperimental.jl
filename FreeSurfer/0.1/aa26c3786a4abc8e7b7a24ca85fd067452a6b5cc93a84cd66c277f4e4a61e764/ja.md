```
show(mri::MRI, mrimod::Union{MRI, Nothing}=nothing)
```

ターミナルウィンドウに`MRI`構造体（画像スライスとヘッダー情報の要約）を表示します。

# 引数:

  * `mri::MRI`: 表示するメイン画像
  * `mrimod:MRI`: メイン画像を変調するためのオプションの画像（例：ベクトルマップを変調するためのFAマップ）

```
disp(mri::MRI, mrimod::Union{MRI, Nothing}=nothing)
```

ターミナルウィンドウでの `MRI` 構造体（画像スライスとヘッダー情報の要約）のクイック表示

# 引数:

  * `mri::MRI`: 表示するメイン画像
  * `mrimod:MRI`: メイン画像を変調するためのオプションの画像（例：ベクトルマップを変調するためのFAマップ）

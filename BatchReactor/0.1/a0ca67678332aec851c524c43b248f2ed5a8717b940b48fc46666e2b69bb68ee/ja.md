これは、ユーザー定義のレート計算を使用してバッチリアクターを実行するための呼び出し関数です。

# 使用法

```
batch_reactor(input_file::AbstractString, lib_dir::AbstractString, user_defined::Function; sens= false)
```

  * input_file: バッチリアクターのためのxml入力ファイル
  * lib_dir: データファイルが存在するディレクトリ。相対パスである必要があります
  * user_defined : 種のソース項を計算する関数。ユーザーによって提供される必要があります
  * sens : 感度コードと一緒に使用する場合はtrueに設定するBoolean

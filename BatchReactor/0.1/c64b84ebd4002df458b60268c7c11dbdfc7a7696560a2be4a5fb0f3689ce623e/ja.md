これは化学入力ファイルを使用してバッチリアクターを実行するための呼び出し関数です。

# 使用法

batch*reactor(input*file::AbstractString, lib_dir::AbstractString; sens= false, surfchem=false, gaschem=false)

  * input_file: バッチリアクターのためのxml入力ファイル
  * lib_dir: データファイルが存在するディレクトリ。相対パスである必要があります
  * sens : 感度コードと一緒に使用する場合はtrueに設定するBoolean
  * surfchem : 表面反応速度の計算を指定するBoolean
  * gaschem : 気相反応速度の計算を指定するBoolean

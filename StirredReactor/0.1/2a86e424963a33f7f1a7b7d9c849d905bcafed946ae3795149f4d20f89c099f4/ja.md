これは、化学入力ファイルを使用してcstrリアクターを実行するための呼び出し関数です。

# 使用法

cstr(input*file::AbstractString, lib*dir::AbstractString; sens= false, surfchem=false, gaschem=false)

  * input_file: バッチリアクターのためのxml入力ファイル
  * lib_dir: データファイルが存在するディレクトリ。相対パスである必要があります
  * sens: 感度計算
  * surfchem : 表面化学。falseは表面化学計算を行わないことを意味します。

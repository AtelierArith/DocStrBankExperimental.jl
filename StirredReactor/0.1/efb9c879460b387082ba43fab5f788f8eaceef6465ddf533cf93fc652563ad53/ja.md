これは、ユーザー定義の反応速度計算を使用してcstrリアクターを実行するための呼び出し関数です。

# 使用法

cstr(input*file::AbstractString, lib*dir::AbstractString; sens= false, surfchem=false, gaschem=false)

  * input_file: バッチリアクターのためのxml入力ファイル
  * lib_dir: データファイルが存在するディレクトリ。相対パスである必要があります
  * user_defined: ユーザーによって提供される種のソース項を計算する関数

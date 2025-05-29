これは、ユーザー定義の反応速度計算を使用してプラグリアクターを実行するための呼び出し関数です。

# メソッド-1

plug(input*file::AbstractString, lib*dir::AbstractString; sens= false, surfchem=false, gaschem=false)

  * input_file: バッチリアクターのためのxml入力ファイル
  * lib_dir: データファイルが存在するディレクトリ。相対パスである必要があります
  * user_defined: ユーザーによって提供される種のソース項を計算する関数

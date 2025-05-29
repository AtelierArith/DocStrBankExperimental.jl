これは、化学入力ファイルを使用してプラグリアクターを実行するための呼び出し関数です。

# メソッド-2

plug(input*file::AbstractString, lib*dir::AbstractString; sens= false, surfchem=false, gaschem=false)

  * input_file: プラグフローリアクター構成のxml入力ファイル
  * lib_dir: データファイルが存在するディレクトリ（メカニズムファイルとtherm.datファイル）。
  * sens: 感度計算
  * surfchem : 表面化学; falseは表面化学計算を行わないことを意味します
  * gaschem : 気相化学; falseは気相化学計算を行わないことを意味します

get_isfemale(filename::String)

制御ファイルをjson形式から`IsFemale`型/構造体を作成します。制御ファイルに性別情報が記載されていない場合、すべて女性であると仮定します (*ref: [qtl2](https://github.com/rqtl/qtl2/blob/main/R/read_cross2.R)* 行 229)。

# 引数

  * `filename` : json形式の制御ファイルの名前（ディレクトリを含む）を含む文字列。

# 出力

`IsFemale`型/構造体を返します。

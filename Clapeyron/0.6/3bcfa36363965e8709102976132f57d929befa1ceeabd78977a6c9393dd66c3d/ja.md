```
ParamOptions(;kwargs...)
```

パラメータ解析に関連するすべてのオプションを含む構造体：

  * `userlocations = String[]`: 検索するユーザー定義の場所のリスト。
  * `group_userlocations = String[]`: 検索するユーザー定義のグループ場所のリスト。
  * `asymmetricparams::Vector{String} = String[]`: `param[i,j] ≠ param[j,i]` に従うペアパラメータのリスト。非対称ペアに設定されていない場合、非対称値は上書きされます！
  * `ignore_headers::Vector{String} = ["dipprnumber", "smiles"]`: 無視されるヘッダーのリスト。
  * `ignore_missing_singleparams::Vector{String} = String[]`: 欠損パラメータ値のチェック（`SingleParam`内）や対角線（`PairParam`内）を無視するパラメータのリスト。
  * `verbose::Bool = false`: `true` の場合、ターミナルに表示される `getparams` によって行われたすべての操作を表示します。これには `CSV.jl` によって発生した警告が含まれます。
  * `species_columnreference::String ="species"`: 成分をチェックするための列名。ペアおよび関連パラメータでは、`#species#1` および `#species#2` をチェックします。ここで `#species#` はこのオプションの値です。
  * `site_columnreference::String ="site"`: 関連パラメータ内のサイトをチェックするための列名。`#site#1` および `#site#2` をチェックします。ここで `#site#` はこのオプションの値です。
  * `normalisecomponents::Bool = true`: `true` の場合、CSVおよび入力成分の文字列の正規化を行います。
  * `n_sites_columns::Dict{String,String} = Dict( "e" => "n_e","e1" => "n_e1","e2" => "n_e2","H" => "n_H")`: サイトの数を調べるための辞書。サイトの数は単一パラメータのCSVファイルの列として保存されます。たとえば、名前 `e` のサイトの数は列 `n_e` で調べられます。
  * `return_sites::Bool = true`: `false` に設定すると、関連パラメータは無視され、サイトは作成されません。たとえそれらが場所のリストに存在していても。
  * `component_delimiter::String = "~|~"`: 一致させる複数の成分名がある場合、この区切り文字で分けます。

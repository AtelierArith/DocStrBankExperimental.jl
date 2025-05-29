```
mapallelesCFtable(mapping file, CF file; filename, columns, delim)
```

入力CFファイルと同じ一致係数を含む新しいDataFrameを作成しますが、修正された分類群名を持ちます。入力CFテーブルの各アレル名は、マッピングファイルに基づいてアレルがマッピングされる種名に置き換えられます。マッピングファイルには、アレルと種の列名が必要です。

オプションの引数:

  * `filename` 結果のCFテーブルを書き込む/保存するためのもの。指定されていない場合、出力データフレームはファイルに保存されません。
  * `columns` 分類群名の列番号。デフォルトは1-4。
  * `CSV.File`が受け入れる任意のキーワード引数。例えば、デフォルトでは`delim=','`：列はカンマで区切られます。ユーザーによって別途指定されない限り、`pool=false`（分類群名を文字列として読み込むため、4つの列を分類群名とより簡単に結合するため）。同じCSV引数が入力ファイル（マッピングファイルとクァルテットファイル）の両方を読み込むために使用されます。

ファイル名の代わりにDataFrameを入力するには、[`mapallelesCFtable!`](@ref)も参照してください。

`filename`が指定されている場合、例えば以下の例のように"quartetCF_speciesNames.csv"など、このファイルは後で`pool=false`オプションで読み込むのが最適です。例:

```julia
mapallelesCFtable("allele-species-map.csv", "allele-quartet-CF.csv";
                  filename = "quartetCF_speciesNames.csv")
df_sp = CSV.read("quartetCF_speciesNames.csv", DataFrame); # DataFrameオブジェクト
dataCF_specieslevel = readtableCF!(df_sp, mergerows=true); # DataCFオブジェクト
```

**任意のレベルの分類群に関する情報を取得する**

```
taxon(name::String)
```

この関数は、GBIF参照分類においてその（科学的）名前で分類群を探します。

オプションの引数は次のとおりです。

  * `rank::Union{Symbol,Nothing}=:SPECIES` – 取得したい分類群のランク。これは制御語彙の一部であり、`：DOMAIN`、`：CLASS`、`：CULTIVAR`、`：FAMILY`、`：FORM`、`：GENUS`、`：INFORMAL`、`：ORDER`、`：PHYLUM`、`：SECTION`、`：SUBCLASS`、`：VARIETY`、`：TRIBE`、`：KINGDOM`、`：SUBFAMILY`、`：SUBFORM`、`：SUBGENUS`、`：SUBKINGDOM`、`：SUBORDER`、`：SUBPHYLUM`、`：SUBSECTION`、`：SUBSPECIES`、`：SUBTRIBE`、`：SUBVARIETY`、`：SUPERCLASS`、`：SUPERFAMILY`、`：SUPERORDER`、および`：SPECIES`のいずれかでなければなりません。
  * `strict::Bool=true` – 一致が厳密であるべきか、あいまいであるべきか

最後に、`kingdom`、`phylum`、`class`、`order`、`family`、および`genus`を使用して、分類の他のレベルを指定することもできます。これらはすべて`String`または`Nothing`であることができます。

一致が見つかった場合、結果は`GBIFTaxon`として返されます。一致が見つからない場合、この関数は`nothing`を返し、警告を表示します。

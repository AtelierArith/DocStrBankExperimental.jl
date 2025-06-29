```
Sources( ;
    consumers   :: Any = nothing, 
    products    :: Any = nothing, 
    marketsizes :: Any = nothing, 
    draws       :: Any = nothing,
)
```

オプションのパラメータで提供されたエントリを持つGrumpsSourcesオブジェクトを作成します。

Grumpsは（潜在的に）4つのデータソースを使用します：消費者レベルのデータ用のデータソース、製品レベルのデータ用のもの、市場規模情報用のもの、そして人口統計のドロー用のものです。データレイアウトについては[Spreadsheet formats](@ref)を参照してください。製品レベルのデータのみが必須ですが、それだけでは不十分です。たとえば、BLP95では製品、市場規模、人口統計に関する情報が必要です。Grumps CLER推定器では4種類のデータすべてが必要です。多項ロジットモデルでは消費者情報と製品情報の両方が必要です。すべての市場に対してすべてのデータが必要なわけではありません。たとえば、いくつかの推定器では、ある市場には消費者レベルのデータがあっても、他の市場にはないことが許容されます。

デフォルトでは、エントリは何もない、文字列、DataFrame、またはSourceFileTypeのいずれかです。エントリが何もない場合、それはそのようなデータが使用されないことを意味します。エントリが文字列の場合、それはカンマ区切りのSourceFileCSVエントリに変換され、文字列名がファイル名になります。他のソースファイルタイプを使用するには、まずSourceFileTypeを作成してください。DataFrameも渡すことができます。何もない場合を除いて、データは最終的に（変換されて）DataFrameになり、そこから解析されます。

*consumers*変数は消費者レベルのデータがどこにあるかを指定し、*products*変数は製品レベルのデータ用、*marketsizes*は市場規模用、*draws*は人口統計のドロー用です。

[`Variables()`](@ref)メソッドを使用して、データソースのフォーマットの方法と推定の仕様を指定します。

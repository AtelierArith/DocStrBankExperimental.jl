```
AbstractDataFrame
```

タブularデータを扱うためのインターフェースをすべての具体的な型が公開する抽象型です。

`AbstractDataFrame`は、列名に`Symbol`または文字列を持つ二次元テーブルです。

DataFrames.jlは、`AbstractDataFrame`のサブタイプである2つの型を定義しています：[`DataFrame`](@ref)と[`SubDataFrame`](@ref)。

# インデクシングとブロードキャスティング

`AbstractDataFrame`は、行と列のセレクタを指定する2つのインデックスを渡すことでインデックス指定できます。許可されるインデックスは、標準配列で使用できるインデックスのスーパーセットです。また、`getproperty`および`setproperty!`関数を使用して、`AbstractDataFrame`の単一の列にアクセスすることもできます。列は整数、`Symbol`、または文字列を使用して選択できます。ブロードキャスティングにおける`AbstractDataFrame`の動作は`Matrix`に似ています。

データフレームの`getindex`、`setindex!`、`getproperty`、`setproperty!`、ブロードキャスティングおよびブロードキャスティング代入の詳細な説明は、マニュアルの["インデクシング"セクション](https://juliadata.github.io/DataFrames.jl/stable/lib/indexing/)に記載されています。

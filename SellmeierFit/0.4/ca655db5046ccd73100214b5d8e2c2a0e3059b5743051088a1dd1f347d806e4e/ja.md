```
RefractiveIndexInfo(material::String, author::String; kwargs...)
```

RefractiveIndex.Infoウェブサイトから屈折率と波長データを含むCSVファイルをダウンロードし、ダウンロードしたファイルのローカルパスを返します。デフォルトでは、ファイル名は`<first author name>.csv`で、`<SellmeierFit package directory>/<material name>/`に保存されます。

`<first author name>`と`<material name>`は、RefractiveIndex.InfoウェブページのURLのデータセットを区別する部分に対応します。たとえば、Malitsonらによって発表された二酸化ケイ素データセットのウェブページはhttps://refractiveindex.info/?shelf=main&book=SiO2&page=Malitsonであり、ここで`SiO2`は`<material name>`、`Malitson`は`<first author name>`です。

# キーワード引数

  * `dir::String=""`: ダウンロードしたファイルが保存されるディレクトリ名。
  * `file::String=""`: ダウンロードしたファイルの名前。
  * `force_download::Bool=false`: ダウンロードを強制する場合はtrue; ファイルがすでに存在する場合はダウンロードを避ける場合はfalse。
  * `max_att::Integer=3`: 最大ダウンロード試行回数。
  * `verbose::Bool=true`: メッセージを表示する場合はtrue; サイレンスする場合はfalse。

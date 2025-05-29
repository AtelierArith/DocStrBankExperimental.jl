```
cpsdata(year::Int, month::Int[, vars::Vector{String}])
```

指定された年と月のCPSマイクロデータファイルをダウンロード/解析し、オプションで指定された変数のみを保持します。数百の変数があるため、必要なものだけを指定することでデータ作業の効率が大幅に向上します。Tables.jlインターフェースでサポートされている任意のデータ型に簡単に変換できるテーブルを返します。

# 引数

  * `year::Int`: CPSデータを取得したい年。
  * `month::Int`: CPSデータを取得したい月。
  * `vars::Vector{String}`: マイクロデータファイル内で保持したい変数を指定するオプションの引数。

# 例

```
data1901 = cpsdata(2019, 1, ["HRINTSTA", "PWORWGT"])
```

データをDataFrameとして扱いたい場合：

```
using DataFrames

data1901 = DataFrame(cpsdata(2019, 1, ["HRINTSTA", "PWORWGT"]))
```

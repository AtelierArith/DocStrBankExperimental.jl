```
writedlm2(f, A; opts...)
writedlm2(f, A, delim; opts...)
```

`A`（ベクトル、行列、または反復可能な行の反復可能コレクション、`Tables`ソース）を`f`（ファイル名またはIOストリーム）にテキストとして書き込みます。列は`';'`で区切られ、別の`delim`（CharまたはString）を定義できます。

デフォルトでは、値の前処理が行われます。文字列として書き込む前に、小数点記号が`'.'`から`','`に変更されます。キーワード引数`decimal=`を使用して、別の小数点記号を定義できます。この前処理をオフにするには、`decimal='.'`を設定します。

`writedlm2()`では、`Date`および`DateTime`データの出力形式をフォーマット文字列で定義できます。デフォルトはISO形式です。日（`E`, `e`）および月（`U`, `u`）の名前は`locale`言語で書かれます。`Complex`数を書くために、虚数成分の接尾辞は`imsuffix=`キーワード引数で選択できます。

# 追加のキーワード引数

  * `decimal=','`: 小数点記号を書くための文字
  * `dtfs="yyyy-mm-ddTHH:MM:SS.s"`: DateTime書き込み形式
  * `dfs="yyyy-mm-dd"`: 日付書き込み形式
  * `locale="english"`: DateTime書き込みの言語
  * `imsuffix="im"`: 複素数の虚数接尾辞 `"im"`, `"i"` または `"j"`
  * `missingstring="na"`: 欠損値の書き方

# コード例

```jldoctest
julia> using ReadWriteDlm2, Dates

julia> A = Any[1 1.2; "text" Date(2017)];

julia> writedlm2("test.csv", A)

julia> read("test.csv", String)
"1;1,2\ntext;2017-01-01\n"
```

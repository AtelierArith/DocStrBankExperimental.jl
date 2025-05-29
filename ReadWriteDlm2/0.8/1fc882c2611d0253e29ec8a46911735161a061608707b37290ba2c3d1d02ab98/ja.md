```
readdlm2(source; options...)
readdlm2(source, T::Type; options...)
readdlm2(source, delim::AbstractChar; options...)
readdlm2(source, delim::AbstractChar, T::Type; options...)
readdlm2(source, delim::AbstractChar, eol::AbstractChar; options...)
readdlm2(source, delim::AbstractChar, T::Type, eol::AbstractChar; options...)
```

`source` から行列を読み込みます。`source` はテキストファイル、ストリーム、またはバイト配列である可能性があります。各行（`eol` で区切られ、デフォルトでは `'\n'`）は1行を提供します。列は `';'` で区切られ、別の `delim` を定義することができます。

`source` の前処理により、正規表現置換が小数点を `d,d` から `d.d` に変更します。デフォルトの `rs` に対してキーワード引数 `decimal=','` は `rs` の `r`-文字列内の小数点文字を設定します。特別な正規表現置換タプル `rs=(r.., s..)` が定義されている場合、引数 `decimal` は使用されません。前処理は次のようにオフにできます: `rs=()`。

標準ライブラリの `readdlm()` に加えて、データは `Dates` 形式、`Time` 形式 `"HH:MM[:SS[.s{1,9}]]"`、および複素数と有理数の解析も行われます。日付/時間の解析を無効にするには、`dfs="", dtfs=""` を設定します。`locale` は日（`E`, `e`）および月（`U`, `u`）の名前の言語を定義します。

結果はデフォルトの要素型 `Any` の（異種）配列になります。`header=true` の場合、データ配列と列名のベクトルを含むタプルになります。データ配列の要素に対して他の（抽象）型を定義することもできます。データが空の場合、`0×0 Array{T,2}` が返されます。

`tables=true`[, `header=true`] オプションで、個々の列型を持つ `Tables` インターフェース互換の `MatrixTable` が返され、例えば `DataFrame()` の引数として使用できます。

# 追加のキーワード引数

  * `decimal=','`: デフォルトの `rs` で使用される小数点文字、`rs` タプルがデフォルトでない場合は無関係
  * `rs=(r"(\d),(\d)", s"\1.\2")`: 正規表現 (r,s) タプル、デフォルトでは `decimal=','` の場合 d,d を d.d に変更
  * `dtfs="yyyy-mm-ddTHH:MM:SS.s"`: DateTime 解析用のフォーマット文字列
  * `dfs="yyyy-mm-dd"`: 日付解析用のフォーマット文字列
  * `locale="english"`: 日付名の解析用の言語
  * `tables=false`: `true` の場合、`Tables` インターフェース互換の MatrixTable を返す
  * `dfheader=false`: 'dfheader=true' は `tables=true, header=true` の短縮形
  * `missingstring="na"`: 欠損値の表現方法

`readdlm()` の機能と（キーワード）引数についての詳細情報は、`readdlm()` の `help` で確認できます。

# コード例

```jldoctest
julia> using ReadWriteDlm2

julia> A = Any[1 1.2; "text" missing];

julia> writedlm2("test.csv", A)

julia> readdlm2("test.csv")
2×2 Array{Any,2}:
 1        1.2
  "text"   missing
```

```
proc_data(xlfile, datafiles, paramsets, procwhole_fn, procsubset_fn, postproc_fn; throwonerr=false) 
    → (; overview, subsets_results, résumé, errors)
```

ユーザーが提供したデータ処理関数を呼び出します。

# 引数

  * `xlfile`: XLSXファイル（ある場合）
  * `datafiles`: データファイルまたはフォルダー（ある場合）
  * `paramsets::Vector{NamedTuple}`: ユーザーがCLI引数として提供したものとExcelファイルに含まれるものからマージされたパラメータ。
  * `procwhole_fn::Union{Nothing, Function}`: 前処理のためのユーザー提供関数
  * `procsubset_fn::Union{Nothing, Function}`: データサブセットを処理するためのユーザー提供関数
  * `postproc_fn::Union{Nothing, Function}`: 後処理のためのユーザー提供関数

# キーワード引数

  * `throwonerr=false`: `true`の場合、エラーが発生すると`Julia`の実行が停止し、エラー情報が表示されます。それ以外の場合は実行が続行され、エラー情報は別のファイルに保存できます。

# 戻り値のNamedTuple

  * `overview::NamedTuple`: `procwhole_fn`関数によって返される`DataFrame`やプロットオブジェクトを含む場合があります。
  * `subsets_results::Vector{NamedTuple}`: 各サブセットに対して`procsubset_fn`によって返される`DataFrame`の行やプロットオブジェクトを含む場合があります。
  * `résumé::NamedTuple`: `postproc_fn`関数によって返される`DataFrame`やプロットオブジェクトを含む場合があります。
  * `errors::Vector{NamedTuple}`: エラーが発生した場合、その情報を収集します。

関数`proc_data`は公開されており、エクスポートされていません。

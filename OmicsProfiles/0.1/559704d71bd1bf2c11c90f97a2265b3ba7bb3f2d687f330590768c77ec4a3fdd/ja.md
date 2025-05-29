```
read_10x(path; make_unique=true, omicsname=:RNA, varnames=[:ensembleid, :genesymbol],
    obsnames=[:barcode], varindex=:genesymbol, obsindex=:barcode)
```

`path`から10xデータセットを読み込み、`AnnotatedProfile`を返します。

# 引数

  * `path::AbstractString`: 10xデータセットフォルダへのパス。
  * `make_unique::Bool`: 与えられた`varindex`がユニークでない場合に`varindex`をユニークにするかどうか。
  * `omicsname::Symbol`: 与えられたシーケンシングデータの名前。
  * `varnames::AbstractVector`: 特徴ファイルのヘッダーまたは列名。
  * `obsnames::AbstractVector`: バーコードファイルのヘッダーまたは列名。
  * `varindex::Symbol`: データフレーム`var`のインデックス。
  * `obsindex::Symbol`: データフレーム`obs`のインデックス。

# 例

```jldoctest
julia> using SnowyOwl

julia> prof = read_10x(SnowyOwl.Dataset.pbmc3k_folder(), varindex=:ensembleid)
AnnotatedProfile (nobs = 2700):
    obs: barcode
RNA => OmicsProfile (nvar = 32738):
    var: ensembleid, genesymbol
    layers: count
```

# GBIF2

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://stable.ecojulia.org/GBIF2.jl/) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://docs.ecojulia.org/GBIF2.jl/) [![Build Status](https://github.com/EcoJulia/GBIF2.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/EcoJulia/GBIF2.jl/actions/workflows/CI.yml?query=branch%3Amain) [![Coverage](https://codecov.io/gh/EcoJulia/GBIF2.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/rafaqz/GBIF2.jl)

GBIF2の目標は、GBIF APIをできるだけ完全かつ正確にフォローすることです。

主な設計機能は次のとおりです：

  * 単一の結果は、`Occurrence`または`Species`型で返され、`object.fieldname`を使用してGBIFフィールドのすべてにアクセスできます。特定のクエリによって返されない場合は、これらはmissingを返します。
  * 複数の結果は、`Occurrence`または`Species`行のTables.jl互換の`Table`として返されます。この`Table`は、`DataFrame`に変換するか、CSV.jlや同様のパッケージを使用して直接ディスクに書き込むことができます。
  * すべてのGBIF列挙キーは、クエリを送信する前に正確性がチェックされるため、正しいクエリのみが送信されます。明確なメッセージがクエリのエラーを指摘します。
  * 元のAPIとは異なり、一度に`300`を超える`limit`が許可されており、複数のリクエストを行い結果を結合することで実現されています。
  * より大きなクエリの場合、ダウンロードリクエストはgbif.orgアカウント認証で処理されます。

## 簡単な例

```julia
julia> using GBIF2, DataFrames

# `species_match`を使用した基本的な種の一致：
julia> sp = species_match("Lalage newtoni");

julia> sp.species
"Coracina newtoni"

julia> sp.synonym
true

julia> sp.vernacularName
missing

# `species`を使用してより詳細なオブジェクトを取得：
julia> sp_detailed = species(sp);

julia> sp_detailed.vernacularName
"Reunion Cuckooshrike"

# 2000年から2020年までの種の最初の2000件の発生を取得：
julia> oc = occurrence_search(sp;
           limit=2000, country=:RE, hasCoordinate=true, year=(2000,2020)
       ) |> DataFrame
2000×83 DataFrame
  Row │ decimalLongitude  decimalLatitude  year    month   day
      │ Float64?          Float64?         Int64?  Int64?  Int64?
──────┼────────────────────────────────────────────────────────────
    1 │          55.5085         -21.0192    2020       1      14
    2 │          55.4133         -20.928     2020       1      23
    3 │          55.4133         -20.928     2020       1      16
    4 │          55.5085         -21.0192    2020       1      14
    5 │          55.4123         -21.0184    2020       1      13
    6 │          55.4133         -20.928     2020       1      28
    7 │          55.4133         -20.928     2020       1      16
  ⋮   │        ⋮                 ⋮           ⋮       ⋮       ⋮
 1994 │          55.4133         -20.928     2017      10      29
 1995 │          55.4123         -21.0184    2017      10      25
 1996 │          55.4123         -21.0184    2017      10      25
 1997 │          55.4123         -21.0184    2017      10      17
 1998 │          55.4123         -21.0184    2017      10      25
 1999 │          55.4123         -21.0184    2017      10      25
 2000 │          55.4123         -21.0184    2017      10      25
```

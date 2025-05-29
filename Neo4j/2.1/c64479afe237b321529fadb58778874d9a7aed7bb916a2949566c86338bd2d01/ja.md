```julia
cypherQuery(conn, cypher, params; elTypes, nRowsElTypeCheck)

```

他のデータベース `targetDb` から、単一または複数のクエリID `queryId` に対する分子識別子を取得し、さらにEnsembl遺伝子、転写産物、ペプチドIDに関する情報（IDやゲノム位置など）を取得します。

### 引数

  * `conn::Neo4j.Connection` : Neo4jグラフDBインスタンスへの有効な接続。
  * `cypher::String` : 表形式のデータを返すCypher `MATCH` クエリ。
  * `params::Pair` : Cypherクエリに渡されるパラメータ。
  * `elTypes::Vector{Type}` : 列の型を手動で提供することができるVector{Type}
  * `nRowsElTypeCheck::Int` : 列のデータ型を決定するために使用される行数（デフォルトは1000）

### 例

```julia-repl
julia> cypherQuery(
         Neo4j.Connection("localhost"),
         "MATCH (p :Person {name: {name}}) RETURN p.name AS Name, p.age AS Age;",
         "name" => "John Doe")

```

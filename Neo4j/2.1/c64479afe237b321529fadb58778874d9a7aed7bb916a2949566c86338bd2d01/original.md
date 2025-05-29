```julia
cypherQuery(conn, cypher, params; elTypes, nRowsElTypeCheck)

```

Retrieve molecular identifier from other databases, `targetDb`, for single or mulitple query IDs, `queryId`, and moreover information on Ensembl gene, transcript and peptide IDs, such as ID and genomic loation.

### Arguments

  * `conn::Neo4j.Connection` : a valid connection to a Neo4j graph DB instance.
  * `cypher::String` : Cypher `MATCH` query returning tabular data.
  * `params::Pair` : parameters which are passed on to the cypher query.
  * `elTypes::Vector{Type}` : column types can be provided manually as a Vector{Type}
  * `nRowsElTypeCheck::Int` : Number of rows which are used to determine column datatypes (defaults to 1000)

### Examples

```julia-repl
julia> cypherQuery(
         Neo4j.Connection("localhost"),
         "MATCH (p :Person {name: {name}}) RETURN p.name AS Name, p.age AS Age;",
         "name" => "John Doe")

```

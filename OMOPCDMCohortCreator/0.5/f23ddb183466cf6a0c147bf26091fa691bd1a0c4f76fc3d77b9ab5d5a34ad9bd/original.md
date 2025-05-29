GenerateTables(conn; inplace = true, exported = false)

Generates Julia representations of all tables found in a given OMOP CDM database.

# Arguments:

  * `dialect::Symbol` - the dialect used for SQL queries (to see what is dialects are available, see here: https://mechanicalrabbit.github.io/FunSQL.jl/stable/reference/#FunSQL.SQLDialect)
  * `schema::String` - the name of the database schema being used.

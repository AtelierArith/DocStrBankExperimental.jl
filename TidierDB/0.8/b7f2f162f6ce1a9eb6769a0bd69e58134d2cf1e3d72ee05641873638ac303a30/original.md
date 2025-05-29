```
db_table(database, table_name, athena_params, delta = false, iceberg = false, alias = "", df_name)
dt(database, table_name, athena_params, delta = false, iceberg = false, alias = "", df_name)
```

`db_table` starts the underlying SQL query struct, adding the metadata and table. If paths are passed directly to `db_table` instead of a  name it will not copy it to memory, but rather read directly from the file. `db_table`  only supports direct file paths to a table. DataFrames  are read as a view. It does not support database file paths such as  `dbname.duckdb`  or  `dbname.sqlite`. Database files must be used with `connect(db, "path_to_db.duckdb")` first  to allow `db_table` to read the db tables.

# Arguments

  * `database`: The Database or connection object
  * `table_name`: tablename as a string (dataframe, name, local path, or URL).     - CSV/TSV       - Parquet     - Json      - Iceberg     - Delta     - S3 tables from AWS or Google Cloud      - Google Sheets spreadsheet link

      * DuckDB and ClickHouse support vectors of paths and URLs.
      * DuckDB and ClickHouse also support use of `*` wildcards to read all files of a type in a location such as:

          * `db_table(db, "Path/to/testing_files/*.parquet")`
      * Use any DuckDB reader "read*csv('file*path', additional arguments allowed)" .
  * `delta`: must be true to read delta files
  * `iceberg`: must be true to read iceberg finalize_ctes
  * `alias`: optional argument when using a `*` wildcard in a file path, that allows user to determine an alias for the data being read in. If empty, it will refer to table as `data`.
  * `df_name` when using a DataFrame as the second argument, a third string argument must be supplied to become the name of the view.

# Example

```jldoctest

julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> dt(db, df, "df_mem");

julia> db_table(db, "main.df_mem");

julia> dt(db, "df_mem" , alias = "my_table");
```

```
@unnest_wider(sql_query, column)
```

ネストされたカラムをワイド形式に展開します。この関数は、ネストされた構造（例：行や配列）を含むカラムを受け取り、それを別々のカラムに展開します。

# 引数

  * `sql_query`: SQLクエリ
  * `column`: ネストされた構造を展開するカラム。

# 例

```jldoctest
julia> db = connect(duckdb());

julia> DuckDB.query(db, "
        CREATE TABLE df3 (
            id INTEGER,
            pos ROW(lat DOUBLE, lon DOUBLE)
        );
        INSERT INTO df3 VALUES
            (1, ROW(10.1, 30.3)),
            (2, ROW(10.2, 30.2)),
            (3, ROW(10.3, 30.1));");

julia> @chain dt(db, :df3) begin
            @unnest_wider(pos)
            @collect
       end
3×3 DataFrame
 Row │ id     lat      lon     
     │ Int32  Float64  Float64 
─────┼─────────────────────────
   1 │     1     10.1     30.3
   2 │     2     10.2     30.2
   3 │     3     10.3     30.1 
julia> @chain dt(db, :df3) begin
            @unnest_wider(pos, names_sep = "_")
            @collect
       end
3×3 DataFrame
 Row │ id     pos_lat  pos_lon 
     │ Int32  Float64  Float64 
─────┼─────────────────────────
   1 │     1     10.1     30.3
   2 │     2     10.2     30.2
   3 │     3     10.3     30.1
```

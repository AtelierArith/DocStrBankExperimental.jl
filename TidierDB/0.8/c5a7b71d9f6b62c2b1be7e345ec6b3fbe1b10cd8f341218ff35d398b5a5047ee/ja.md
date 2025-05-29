```
@unnest_longer(sql_query, columns...)
```

指定された列を長い形式に展開します。この関数は、配列や他のネストされた構造を含む複数の列を受け取り、それらを長い形式に展開します。配列の各要素が別々の行になります。

# 引数

  * `sql_query`: SQLクエリ
  * `columns...`: アンネストされる配列や他のネストされた構造を含む1つ以上の列。

# 例

```jldoctest
julia> db = connect(duckdb());

julia> DuckDB.query(db, "
            CREATE TABLE nt (
                id INTEGER,
                data ROW(a INTEGER[], b INTEGER[])
                );
            INSERT INTO nt VALUES
                (1, (ARRAY[1,2], ARRAY[3,4])),
                (2, (ARRAY[5,6], ARRAY[7,8,9])),
                (3, (ARRAY[10,11], ARRAY[12,13]));");

julia> @chain dt(db, :nt) begin 
        @unnest_wider data  
        @unnest_longer a b 
        @collect
       end
7×3 DataFrame
 Row │ id     a        b     
     │ Int32  Int32?   Int32 
─────┼───────────────────────
   1 │     1        1      3
   2 │     1        2      4
   3 │     2        5      7
   4 │     2        6      8
   5 │     2  missing      9
   6 │     3       10     12
   7 │     3       11     13

julia> @chain dt(db, :nt) begin 
        @unnest_wider data  
        @unnest_longer a:b 
        @collect
       end
7×3 DataFrame
 Row │ id     a        b     
     │ Int32  Int32?   Int32 
─────┼───────────────────────
   1 │     1        1      3
   2 │     1        2      4
   3 │     2        5      7
   4 │     2        6      8
   5 │     2  missing      9
   6 │     3       10     12
   7 │     3       11     13
```

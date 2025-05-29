```
@unnest_wider(df, columns, names_sep)
```

指定された配列または辞書の列を、個別の列を持つ広い形式のデータフレームに展開します。

# 引数

  * `df`: データフレーム。
  * `columns`: 展開する列。これらの列には配列、辞書、データフレーム、またはタプルが含まれている必要があります。辞書の見出しは列名に変換されます。
  * `names_sep`: 新しい列名を作成するための区切り文字を指定するオプションの文字列。指定しない場合は、デフォルトで `_` になります。

# 例

```jldoctest
julia> df = DataFrame(name = ["Zaki", "Farida"], attributes = [
               Dict("age" => 25, "city" => "New York"),
               Dict("age" => 30, "city" => "Los Angeles")]);

julia> @unnest_wider(df, attributes)
2×3 DataFrame
 Row │ name    attributes_city  attributes_age 
     │ String  String           Int64          
─────┼─────────────────────────────────────────
   1 │ Zaki    New York                     25
   2 │ Farida  Los Angeles                  30

julia> df2 = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7, 8]])
2×3 DataFrame
 Row │ a      b       c      
     │ Int64  Array…  Array… 
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7, 8]

julia> @unnest_wider(df2, b:c, names_sep = "")
2×5 DataFrame
 Row │ a      b1     b2     c1     c2    
     │ Int64  Int64  Int64  Int64  Int64 
─────┼───────────────────────────────────
   1 │     1      1      2      5      6
   2 │     2      3      4      7      8


julia> a1=Dict("a"=>1, "b"=>Dict("c"=>1, "d"=>2)); a2=Dict("a"=>1, "b"=>Dict("c"=>1)); a=[a1;a2]; df=DataFrame(a);

julia> @unnest_wider(df, b)
2×3 DataFrame
 Row │ a      b_c    b_d     
     │ Int64  Int64  Int64?  
─────┼───────────────────────
   1 │     1      1        2
   2 │     1      1  missing 

julia> a0=Dict("a"=>0, "b"=>0);  a1=Dict("a"=>1, "b"=>Dict("c"=>1, "d"=>2)); a2=Dict("a"=>2, "b"=>Dict("c"=>2)); a3=Dict("a"=>3, "b"=>Dict("c"=>3)); a=[a0;a1;a2;a3]; df3=DataFrame(a);

julia> @unnest_wider(df3, b)
4×3 DataFrame
 Row │ a      b_c      b_d     
     │ Int64  Int64?   Int64?  
─────┼─────────────────────────
   1 │     0  missing  missing 
   2 │     1        1        2
   3 │     2        2  missing 
   4 │     3        3  missing 

julia> df = DataFrame(x1 = ["one", "two", "three"], x2 = [(1, "a"), (2, "b"), (3, "c")])
3×2 DataFrame
 Row │ x1      x2       
     │ String  Tuple…   
─────┼──────────────────
   1 │ one     (1, "a")
   2 │ two     (2, "b")
   3 │ three   (3, "c")

julia> @unnest_wider df x2
3×3 DataFrame
 Row │ x1      x2_1   x2_2   
     │ String  Int64  String 
─────┼───────────────────────
   1 │ one         1  a
   2 │ two         2  b
   3 │ three       3  c
```

```
@unnest_wider(sql_query, column)
```

ネストされた列を広い形式に展開します。この関数は、ネストされた構造（例：行や配列）を含む列を取り、それを別々の列に展開します。

# 引数

  * `sql_query`: SQLクエリ
  * `column`: 展開するネストされた構造を含む列。

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

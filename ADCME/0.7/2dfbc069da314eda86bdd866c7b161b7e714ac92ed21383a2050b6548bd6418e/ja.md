```
execute(db::Database, sql::String, args...)
```

データベース `db` で SQL ステートメント `sql` を実行します。ユーザーは do ブロック構文を使用することもできます。

```julia
execute(db) do 
    "create table mytable (a real, b real)"
end
```

`execute` はレコードのバッチを挿入するためにも使用できます。

```julia
t1 = rand(10)
t2 = rand(10)
param = collect(zip(t1, t2))
execute(db, "INSERT TO mytable VALUES (?,?)", param)
```

または 

```julia
execute(db, "INSERT TO mytable VALUES (?,?)", t1, t2)
```

```
Database(filename::Union{Missing, String} = missing; 
    commit_after_execute::Bool = true)
```

`filename`からデータベースを作成します。`filename`が提供されていない場合、メモリ内データベースが作成されます。`commit_after_execute`がfalseの場合、各[`execute`](@ref)の後にコミット操作は行われません。

  * doブロック構文:

```julia
Database() do db
    execute(db, "create table mytable (a real, b real)")
end
```

データベースは実行後に自動的に閉じられます。したがって、executeがクエリ操作である場合、ユーザーは結果をグローバル変数に保存する必要があります。

  * クエリメタ情報

```julia
keys(db) # すべてのテーブル 
keys(db, "mytable") # `db.mytable`のすべての列名 
```

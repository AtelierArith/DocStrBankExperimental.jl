```
pkeys(itr::IndexedTable)
```

テーブルの主キー。テーブルに指定された主キー列がない場合（`pkey`引数なしで構築された場合）、デフォルトのキーとしてタプル `(1,):(n,)` が生成されます。

# 例

```
a = table(["a","b"], [3,4]) # pkeyなし
pkeys(a)

a = table(["a","b"], [3,4], pkey=1)
pkeys(a)
```

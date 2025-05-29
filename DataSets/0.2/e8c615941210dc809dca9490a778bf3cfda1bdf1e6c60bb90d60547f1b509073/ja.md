```
@datafunc function f(x::DT=>T, y::DS=>S...)
    ...
end
```

関数 `f(x::T, y::S, ...)` を定義し、データディスパッチルールを追加して、`f(x::DataSet, y::DataSet)` がデータセットタイプ `DT,DS` に一致するデータセットを Julia タイプ `T,S` として開くようにします。

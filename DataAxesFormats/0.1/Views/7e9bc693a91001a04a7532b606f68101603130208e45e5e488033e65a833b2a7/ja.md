```
viewer(
    daf::DafReader;
    [name::Maybe{AbstractString} = nothing,
    axes::Maybe{ViewAxes} = nothing,
    data::Maybe{ViewData} = nothing]
)::DafReadOnly
```

`daf` データを読み取り専用 [`DafView`](@ref) でラップします。公開されたビューは、元のデータに適用される一連のクエリによって定義されます。これらのクエリは、データが実際にアクセスされるときにのみ評価されます。したがって、ビューを作成することは比較的安価な操作です。

`name` が指定されていない場合、結果の名前は `daf` の名前に基づき、`.view` サフィックスが付加されます。

クエリは、軸とデータのために別々にリストされます。

!!! note
    最適化として、すべての引数が空（デフォルト）の場合に `viewer` を呼び出すと、単純な [`DafReadOnlyWrapper`](@ref) が返されます。つまり、これは [`read_only`](@ref) を呼び出すことと同等です。さらに、`data = ALL_DATA` と指定すると、公開された任意の軸を使用してすべてのデータが公開されます。特定のデータをその `key` に基づいて隠すには、`data = [ALL_DATA..., key => nothing]` と書くことができます。


与えられた反復可能なオブジェクト内のすべての量子ビットなしで、指定された安定器を返します。

結果の表は、その交換関係を保持することが保証されていません。

```jldoctest
julia> delete_columns(S"XYZ YZX ZXY", [1,3])
+ Y
+ Z
+ X
```

参照: [`traceout!`](@ref)

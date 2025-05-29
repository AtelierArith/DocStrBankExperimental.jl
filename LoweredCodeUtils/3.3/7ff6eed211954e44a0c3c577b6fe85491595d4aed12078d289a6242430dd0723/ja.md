```
isrequired = lines_required(obj::GlobalRef, src::CodeInfo, edges::CodeEdges)
isrequired = lines_required(idx::Int,                     src::CodeInfo, edges::CodeEdges)
```

`obj`または`idx`でインデックスされたステートメントを評価するために実行する必要がある行を特定します。`isrequired[i]`が`false`の場合、`i`番目のステートメントは*必要ありません*。ある状況では、`true`でマークされたすべてのステートメントが必要な場合がありますが、他の状況では制御フローがそのようなステートメントのサブセットをスキップし、他のステートメントを複数回繰り返すことになります。

[`lines_required!`](@ref)および[`selective_eval!`](@ref)も参照してください。

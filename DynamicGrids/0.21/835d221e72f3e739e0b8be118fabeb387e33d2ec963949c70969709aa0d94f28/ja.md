```
SetNeighborhoodRule <: SetRule
```

[`SetRule`](@ref) は、その近傍にのみ書き込み、境界チェックを必要としないものです。

[`positions`](@ref) と [`offsets`](@ref) は、近傍の値を変更するための便利なイテレータです。

`SetNeighborhoodRule` ルールは、関数 `neighborhood(rule)` から [`Neighborhood`](@ref) オブジェクトを返さなければなりません。デフォルトでは、これは `rule.neighborhood` です。このプロパティが存在する場合、インターフェースメソッドは必要ありません。

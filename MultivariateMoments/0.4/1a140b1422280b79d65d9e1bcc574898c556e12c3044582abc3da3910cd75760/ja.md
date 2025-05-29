```
struct StaircaseDependence
    standard_or_corner::Bool
    linear::LinearDependence
end
```

基底の要素の依存関係は、[`MacaulayNullspace`]の行のインデックスを表します。フィールド`standard_or_corner`がtrueの場合、要素は標準またはコーナーのいずれかです（`linear`フィールドにエンコードされた線形依存関係に依存します）。そうでない場合、それはコーナーではない境界であるか、境界ですらない可能性があります。`linear`フィールドについては、[`LinearDependence`](@ref)を参照してください。

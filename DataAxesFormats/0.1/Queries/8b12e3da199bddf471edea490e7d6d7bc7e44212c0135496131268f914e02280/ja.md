```
Or(property::AbstractString) <: QueryOperation
```

[`Axis`](@ref) のエントリのセットを拡張するためのクエリ操作です。文字列の [`Query`](@ref) では、`|` 演算子を使用し、マスクを計算するために参照する軸プロパティの名前を続けて指定します。

これは [`And`](@ref) と似ていますが、マスクに追加します（例：`/ gene & is_marker | is_noisy` は、結果ベクトルをマーカーまたはノイジーな遺伝子のいずれかに制限します）。

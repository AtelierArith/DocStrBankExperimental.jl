```
Lookup(property::AbstractString) <: Query
```

名前を持つプロパティの値を検索するためのクエリ操作です。文字列 [`Query`](@ref) では、`:` 演算子の後に検索するプロパティ名を指定します。

  * クエリ状態が空の場合、これはスカラー プロパティの値を検索します (例: `: version`)。
  * クエリ状態に単一の軸が含まれている場合、これはベクトル プロパティの値を検索します (例: `/ cell : batch`)。
  * クエリ状態に二つの軸が含まれている場合、これは行列プロパティの値を検索します (例: `/ cell / gene : UMIs`)。

プロパティが存在しない場合、これはエラーになりますが、[`IfMissing`](@ref) に続く場合は除きます (例: `: version || 1.0`)。

軸のいずれかが [`IsEqual`](@ref) を使用して単一のエントリを選択している場合、これは結果の次元を減少させます (例: `/ cell / gene = FOX1 : UMIs` はベクトルであり、`/ cell = C1 / gene = FOX1 : UMIs` と `/ gene = FOX1 : is_marker` はスカラーです)。

!!! note
    これ、[`Names`](@ref) および [`Axis`](@ref) は、完全な [`Query`](@ref) としても機能する唯一の [`QueryOperation`](@ref) です。


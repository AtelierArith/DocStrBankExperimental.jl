```
struct PRange{A}
```

`PRange`（パーティション範囲）は、インデックス `1:n` の範囲をいくつかの部分に分割して表す型です。この型は、[`PVector`](@ref) および [`PSparseMatrix`](@ref) のインスタンスの軸を表すために使用されます。

# プロパティ

  * `partition::A`

アイテム `partition[i]` は、部分番号 `i` の所有、ゴースト、およびローカルインデックスに関する情報を含むオブジェクトです。`typeof(partition[i])` は、[`AbstractLocalIndices`](@ref) インターフェースのメソッドを実装する型です。このインターフェースを使用して、所有、ゴースト、およびローカルインデックスに関する基礎情報にアクセスします。

# スーパタイプ階層

```
PRange{A} <: AbstractUnitRange{Int}
```

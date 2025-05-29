```
struct PSparseMatrix{V,B,C,D,T}
```

`PSparseMatrix`（パーティションスパース行列）は、行が異なる部分に分配（すなわち、パーティション）されている行列を表す型で、分散メモリ並列計算のために使用されます。各部分は行列の行のサブセットと、それに対応する非ゼロ列を格納します。

この型は、対応する並列実装を持つ多数の配列のような操作をオーバーロードします。

# プロパティ

  * `matrix_partition::A`
  * `row_partition::B`
  * `col_partition::C`
  * `assembled::Bool`

`matrix_partition[i]` には、部分番号 `i` におけるローカル行と対応する非ゼロ列（ローカル列）を持つ（スパース）行列が含まれています。 `eltype(matrix_partition) == V`。 `row_partition[i]` と `col_partition[i]` には、部分番号 `i` におけるローカル、自身、ゴースト行および列に関する情報が含まれています。 `eltype(row_partition)` と `eltype(col_partition)` の型は [`AbstractLocalIndices`](@ref) インターフェースを実装しています。 `assembled==true` の場合、行列データは自身の行に完全に含まれていると仮定されます。

# スーパークラス階層

```
PSparseMatrix{V,A,B,C,T} <: AbstractMatrix{T}
```

ここで `T=eltype(V)` です。

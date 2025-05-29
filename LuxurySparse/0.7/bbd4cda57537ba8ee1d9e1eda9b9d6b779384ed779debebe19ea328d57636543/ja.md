```
SparseMatrixCOO(is::Vector, js::Vector, vs::Vector, m::Int, n::Int) -> SparseMatrixCOO
SparseMatrixCOO{Tv, Ti}(is::Vector{Ti}, js::Vector{Ti}, vs::Vector{Tv}, m::Int, n::Int) -> SparseMatrixCOO
```

COOrdinate形式の疎行列。

値`vs`は、`m`行`n`列の行列の行`is`と列`js`に追加されます。

「ijv」または「トリプレット」形式とも呼ばれます。

# 注意事項

COO行列は、加算、減算、乗算、除算、行列の累乗などの算術演算には使用しないでください。

### COO形式の利点

  * 疎な形式間の高速変換を促進します
  * 重複エントリを許可します（例を参照）
  * CSR/CSC形式への非常に高速な変換を提供します（CSRは実装されていません）

### COO形式の欠点

直接サポートしていません：

  * 算術演算
  * スライス

### 意図された使用法

  * COOは疎行列を構築するための高速形式です
  * 行列が構築されたら、迅速な算術および行列ベクトル演算のためにCSRまたはCSC形式に変換します
  * CSRまたはCSC形式に変換する際、デフォルトでは重複する(i,j)エントリが合計されます。これにより、有限要素行列などの効率的な構築が促進されます。（例を参照）

# 例

```julia-repl
julia> SparseMatrixCOO([4,3,1,2,2], [2,3,1,4,4], [1,2,3,4,5], 4,4) # 重複エントリ(2,4)が合計されます
4×4 SparseMatrixCOO{Int64, Int64}:
 3  0  0  0
 0  0  0  9
 0  0  2  0
 0  1  0  0

```

`svd_embedding(A,svd_engine,d)`

隣接行列 `A` の次元 `d` の SVD 埋め込みを計算し、`svd_engine` を使用して SVD 分解を行います。

隣接行列 A が与えられると、この関数は特異値分解を使用してノード埋め込みを返します。これはランダムドットプロダクトグラフで行われるように行われます。この関数は、デフォルトの `LinearAlgebra` からの `svd()` とは異なるユーザー定義の `svd_engine` を受け入れます。その場合、`svd_engine` は `truncated_svd` と同じ形式の関数でなければなりません。

# 引数

  * `A`: 埋め込むグラフの隣接行列。
  * `d`: `Int` の場合、埋め込みの次元。何も指定しない場合、関数は Zhu&Ghodsi メソッドを使用して最適な埋め込み次元を推定します。または、埋め込みの最適次元を返すユーザー定義の関数であることもできます。
  * `svd_engine`: SVD 分解を実行するために使用される関数で、デフォルトは `LinearAlgebra` の `svd()` です。

# 注意事項

  * 行列 `A` は非対称（すなわち、グラフは有向である可能性があります）および長方形（例：二部グラフ）である可能性があります。

# 例

```julia
julia> # まず 2 ブロックの行列を構築します:
julia> block_matrix = reshape([ones(5,5) zeros(5,5); zeros(5,5) ones(5,5)],10,10)
julia> # 次に、次元を指定して分解します
julia> L,R = svd_embedding(block_matrix,4)
julia> # または自動的に
julia> L,R = svd_embedding(block_matrix)

```

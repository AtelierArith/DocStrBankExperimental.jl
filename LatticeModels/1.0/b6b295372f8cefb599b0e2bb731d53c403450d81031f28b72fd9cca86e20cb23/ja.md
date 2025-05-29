```
diagonalize(op::DataOperator[, routine; params...])
```

`Operator`の固有値と固有ベクトルを見つけ、それらを`Eigensystem`に格納します。

利用可能な2つのルーチンがあります：

  * `:lapack`は、標準の`LinearAlgebra`パッケージの`eigen`関数を使用します。
  * `:krylovkit`は、`KrylovKit`パッケージのランチョスアルゴリズムを使用します。以下のパラメータを受け入れます：

      * `v0`は開始ベクトルです。デフォルトは`rand(ComplexF64, size(op.data, 1))`です。
      * `n`は目標の固有ベクトルの数です。デフォルトは10です。

    その他のキーワード引数は`KrylovKit.eigsolve`関数に渡されます。詳細についてはそのドキュメントを参照してください。
  * `:auto`は、演算子のサイズに基づいて自動的にルーチンを選択します。

デフォルトのルーチンは、密な演算子に対して`:lapack`です。演算子行列が5000×5000未満の場合、自動的に密な演算子に変換されます。それ以外の場合は`:krylovkit`が使用されます。

## 例

```jldoctest
julia> using LatticeModels

julia> l = SquareLattice(4, 4);

julia> H = tightbinding_hamiltonian(l)
Hamiltonian(dim=16x16)
System: One particle on 16-site SquareLattice in 2D space
16×16 SparseArrays.SparseMatrixCSC{ComplexF64, Int64} with 48 stored entries:
⎡⠪⡢⠑⢄⠀⠀⠀⠀⎤
⎢⠑⢄⠪⡢⠑⢄⠀⠀⎥
⎢⠀⠀⠑⢄⠪⡢⠑⢄⎥
⎣⠀⠀⠀⠀⠑⢄⠪⡢⎦

julia> eig = diagonalize(H)
Diagonalized Hamiltonian (16 eigenvectors)
Eigenvalues in range -3.23607 .. 3.23607
System: One particle on 16-site SquareLattice in 2D space
```

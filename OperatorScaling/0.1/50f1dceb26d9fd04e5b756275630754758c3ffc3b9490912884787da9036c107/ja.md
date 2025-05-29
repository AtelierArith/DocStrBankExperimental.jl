```
equilibrate!(A::AbstractMatrix{T},
             D1::Diagonal{T, S}, D2::Diagonal{T, S},
             R_k::Diagonal{T, S}, C_k::Diagonal{T, S};
             ϵ::T = T(1.0e-2), max_iter::Int = 100,
             A_transposed::Bool = false) where {T, S <: AbstractVector{T}}
```

行列 `A` のスケーリングを行い、その行と列が無限ノルム1を持つようにする平衡化アルゴリズムを実行します。`D1` と `D2` はそれぞれサイズ `size(A, 1)` と `size(A, 2)` の対角スケーリング因子です。`A` がスケーリングされると、恒等式 `inv(D1) * A * inv(D2)` によりスケーリングされていない行列が得られます。`R_k` と `C_k` はそれぞれサイズ `size(A, 1)` と `size(A, 2)` の対角行列で、事前に割り当てる必要があります。`max_iter` は最大反復回数です。

`A_transposed = true` の場合、`A` がスケーリングされると、恒等式 `inv(D2) * A * inv(D1)` によりスケーリングされていない行列が得られます。`A_transposed = true` を使用する場合、`D1` と `D2` はそれぞれサイズ `size(A, 2)` と `size(A, 1)` である必要があります。

```
equilibrate!(Q::Symmetric{T}, D::Diagonal{T, S}, C_k::Diagonal{T, S};
             ϵ::T = T(1.0e-2), max_iter::Int = 100) where {T, S <: AbstractVector{T}}
```

対称行列 `Q` のスケーリングを行い、その行と列が無限ノルム1を持つようにする平衡化アルゴリズムを実行します。`D` はサイズ `size(Q, 1)` の対角スケーリング因子です。`Q` がスケーリングされると、恒等式 `inv(D) * Q * inv(D)` によりスケーリングされていない行列が得られます。`C_k` はサイズ `size(A, 1)` の対角行列で、事前に割り当てる必要があります。`max_iter` は最大反復回数です。

# 参考文献

  * D. Ruiz, *A Scaling Algorithm to Equilibrate Both Rows and Columns Norms in Matrices*, RAL-TR-2001-034, 2001.

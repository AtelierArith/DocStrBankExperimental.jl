```
block_tridgm(main_diag::Vector{Matrix{T}}, upper_diag::Vector{Matrix{T}}, lower_diag::Vector{Matrix{T}}) where {T<:Real}
```

3つの行列のベクトルからブロックトリジオナル行列を構築します。

# 引数

  * `main_diag::Vector{Matrix{T}}`: 主対角線のための行列のベクトル。
  * `upper_diag::Vector{Matrix{T}}`: 上部対角線のための行列のベクトル。
  * `lower_diag::Vector{Matrix{T}}`: 下部対角線のための行列のベクトル。

# 戻り値

  * ブロックトリジオナル行列を表す疎行列。

# 例外

  * `ErrorException` は、`upper_diag` と `lower_diag` の長さが `main_diag` の長さより1少ない場合にスローされます。

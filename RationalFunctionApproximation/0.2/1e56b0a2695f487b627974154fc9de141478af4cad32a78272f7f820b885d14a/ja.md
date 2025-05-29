```
DiscretizedPath(path, s::AbstractVector; kwargs...)
DiscretizedPath(path, n::Integer=0; kwargs...)
```

パスを離散化し、将来的にローカルな細分化を行うオプションを保持します。

# 引数

  * `path`: ComplexCurve または ComplexPath
  * `s`: パラメータ値のベクトル
  * `n`: パスを離散化するポイントの数

# キーワード引数

  * `refinement`: 連続するポイント間で行う細分化の数
  * `maxpoints`: 許可される最大ポイント数

他に [`collect`](@ref), [`add_node!`](@ref) を参照してください。

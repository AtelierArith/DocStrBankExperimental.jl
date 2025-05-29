```
warp(source::AbstractSampler; kwargs...)
```

サンプラー `source` からサンプリングする前に、サンプラーのドメインワーピングを行う修飾子サンプラーを構築します。

ドメインワーピングは、他のサンプラーの出力をサンプラーの入力に供給します。この修飾子では、各入力座標が異なるサンプラーを指定してワーピングできます。

`x`、`y`、`z`、または `w` にサンプラーが供給されていない場合は、定数ゼロを出力するサンプラーが代わりに使用されます。

# 引数

  * `x::AbstractSampler=constant_1d()`: X軸をワーピングするためのサンプラー。
  * `y::AbstractSampler=constant_1d()`: Y軸をワーピングするためのサンプラー。
  * `z::AbstractSampler=constant_1d()`: Z軸をワーピングするためのサンプラー。
  * `w::AbstractSampler=constant_1d()`: W軸をワーピングするためのサンプラー。

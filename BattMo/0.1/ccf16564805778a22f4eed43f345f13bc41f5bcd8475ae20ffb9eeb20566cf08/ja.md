```julia
mergeInputParams(inputparams1::T, inputparams2::T; warn = false) where {T <: DictInputParams}

# 引数

  * `inputparams1  ::T` : 最初の入力パラメータ構造体
  * `inputparams2  ::T` : 2番目の入力パラメータ構造体
  * `warn = false` : オプション `warn` が true の場合、同じフィールドに対して異なる2つの値が与えられたときに警告を出します。最初の値が優先されます。

# 戻り値

2つの入力パラメータ構造体のフィールドを合成した `DictInputParams` 構造体。
```

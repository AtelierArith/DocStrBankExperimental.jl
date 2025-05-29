```
update_se_hessian!(
    partable::AbstractParameterTable,
    fit::SemFit;
    method = :finitediff)
```

`fit`のために計算されたヘッセ行列の標準誤差を`partable`の`:se`列に書き込みます。

# 引数

  * `method::Symbol`: ヘッセ行列を計算する方法、詳細については[se_hessian](@ref)を参照してください。

# 例

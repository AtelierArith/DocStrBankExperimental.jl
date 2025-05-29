```
param_indices(semobj)
```

`semobj`内のパラメータラベルとそのインデックスの辞書を返します。

# 例

```julia
parind = param_indices(my_fitted_sem)
parind[:param_name]
```

関連情報は[`params`](@ref)を参照してください。

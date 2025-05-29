```
@check_error_code expr
```

`expr`が`zero(PetscErrorCode)`に等しいエラーコードを返すかどうかを確認します。そうでない場合は、[`PetscError`](@ref)のインスタンスをスローします。

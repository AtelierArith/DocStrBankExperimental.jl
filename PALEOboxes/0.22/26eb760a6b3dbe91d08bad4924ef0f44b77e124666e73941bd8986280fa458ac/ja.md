```
get_variables(domain; hostdep=nothing, vfunction=VF_Undefined) -> Vector{VariableDomain}
```

ドメイン変数を取得し、オプションで `hostdep` および `:vfunction` 属性に基づいてサブセットをフィルタリングします。

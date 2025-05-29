```
updateparam(P::Process, p::Integer, profile::Function)
updateparam(P, p, value::Union{Number, Tuple, Vector})
updateparam(P, p, profile, value)
```

新しい `:parameter_profiles` と `:parameter_profile_parameters` のセットで [`Process`](@ref) をコピーします。`p` は更新するパラメータを指定する整数で、`profile` は新しいプロファイルで、`value` には新しい `:parameter_profile_parameters` が含まれます。

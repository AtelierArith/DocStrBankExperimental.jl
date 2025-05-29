```
set_infinite_domain(prefs::AbstractArray{<:GeneralVariableRef},
                 domain::InfiniteArrayDomain)::Nothing
```

依存する無限パラメータ `prefs` の多次元無限ドメインを `domain` に指定します。これにより、基盤となる [`DependentParameters`](@ref) オブジェクトに含まれるすべてのサポートがリセット/削除されます。すべての依存する無限パラメータが含まれていない場合や、いずれかが測定に使用されている場合はエラーになります。`prefs` が依存する無限パラメータでない場合は `ArgumentError` がスローされます。

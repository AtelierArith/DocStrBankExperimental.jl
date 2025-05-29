```
generate_support_values(domain::AbstractInfiniteDomain,
                        [method::Type{MyMethod} = MyMethod];
                        [num_supports::Int = DefaultNumSupports,
                        sig_digits::Int = DefaultSigDigits]
                        )::Tuple{Array{<:Real}, Symbol}
```

[`generate_supports`](@ref) のための多重ディスパッチメソッドです。これは、最初の要素がサポートで、2番目がそのラベルであるタプルを返します。これは、ユーザー定義の無限ドメインおよび/または生成メソッドに対して拡張できます。新しいドメインタイプを定義する際、デフォルトのメソッドディスパッチは `method` をオプション引数にする必要があります（デフォルトとして）。そうでない場合、特定のドメインに対する他のメソッドディスパッチは、`method` をデフォルト値のない位置引数として確保する必要があります（上記の定義とは対照的に）。`method` は、[`PublicLabel`](@ref) または [`InternalLabel`](@ref) のいずれかのサブタイプである必要があることに注意してください。

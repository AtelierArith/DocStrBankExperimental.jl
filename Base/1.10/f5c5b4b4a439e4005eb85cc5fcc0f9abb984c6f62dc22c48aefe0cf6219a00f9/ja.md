```
WeakKeyDict([itr])
```

`WeakKeyDict()` は、キーがオブジェクトへの弱い参照であるハッシュテーブルを構築します。これにより、ハッシュテーブル内で参照されていても、オブジェクトはガーベジコレクトされる可能性があります。

さらなるヘルプについては [`Dict`](@ref) を参照してください。なお、[`Dict`](@ref) とは異なり、`WeakKeyDict` は挿入時にキーを変換しません。これは、キーオブジェクトが挿入前にどこにも参照されていなかったことを意味します。

また、[`WeakRef`](@ref) も参照してください。

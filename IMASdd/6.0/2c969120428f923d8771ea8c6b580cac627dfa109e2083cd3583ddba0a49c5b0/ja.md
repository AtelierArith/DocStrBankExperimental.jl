```
deleteat!(@nospecialize(ids::T), identifier_name::Symbol, conditions::Pair{String}...)::T where {T<:IDSvector}
```

`index_2_name(ids)`の`index`に基づいて一致するすべてのエントリを削除します。

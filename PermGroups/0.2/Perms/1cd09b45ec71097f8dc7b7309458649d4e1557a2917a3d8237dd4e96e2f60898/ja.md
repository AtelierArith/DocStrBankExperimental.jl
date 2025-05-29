`Perm{T}(x::Integer...)where T<:Integer`

はサイクルを返します。例えば、 `Perm{Int8}(1,2,3)` はサイクル `(1,2,3)` を `Perm{Int8}` として構築します。 `{T}` を省略した場合は `{Int16}` が使用されます。

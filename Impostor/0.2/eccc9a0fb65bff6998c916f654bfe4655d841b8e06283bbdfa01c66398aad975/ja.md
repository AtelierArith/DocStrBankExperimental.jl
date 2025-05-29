```
is_locale_available(p::T, c::T, l::T) :: Bool where {T <: AbstractString}
```

提供されたロケール `l` がプロバイダー `p` からのコンテンツ `c` に対して利用可能かどうかを返します。

# パラメータ

  * `p::AbstractString`: プロバイダー名
  * `c::AbstractString`: コンテンツ名
  * `l::AbstractString`: ロケール名

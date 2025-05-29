```
generation(x::SurrealFinite)
```

サロゲート数の誕生日を見つけます。これは、1 + その構成要素の最大値です。

## 引数

  * `x::SurrealFinite`: 操作する数

## 例

```jldoctest
julia> generation( convert(SurrealFinite, 1) )
1
```

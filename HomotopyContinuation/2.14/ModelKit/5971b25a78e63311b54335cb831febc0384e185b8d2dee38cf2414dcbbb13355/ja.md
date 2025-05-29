```
@unique_var variable1 variable2
```

これは[`@var`](@ref)に似ていますが、唯一の違いはマクロが変数の名前を自動的に変更して一意性を確保することです。ただし、バインディングは依然として宣言された名前に対して行われます。これは、名前の衝突がないことを保証するのに役立ちます。

## 例

```julia-repl
julia> @unique_var a b
(a#591, b#592)

julia> a
a#591

julia> b
b#592
```

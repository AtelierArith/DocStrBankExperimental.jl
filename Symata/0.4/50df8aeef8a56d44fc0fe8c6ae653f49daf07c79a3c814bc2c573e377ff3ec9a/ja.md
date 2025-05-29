```
@sym expr
```

JuliaコードにSymata式`expr`を埋め込みます。

Juliaコードに埋め込まれた`expr`を読み取り、評価します。

```
julia> a = 1       # Juliaシンボル`a`
julia> @sym a = 2  # Symataシンボル
julia> a
1
julia> @sym a
2
```

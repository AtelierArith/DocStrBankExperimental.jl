```julia
rename(ft, changes)

```

`FunctionalTable`の列の名前を変更します。第二引数は`src = dest`ペアの`NamedTuple`である必要があり、`dest`はシンボルです。

# 例

```julia
rename(ft, (α = :a, β = :b)) # `α`を`a`に、`β`を`b`に変更します
```

```
@ref_into [:mut] var = mutex[]
```

ミューテックス内の保護された値への参照を作成します。

`:mut` が指定されている場合、可変参照を作成します。そうでない場合、不変参照を作成します。

# 例

```julia
m = Mutex([1, 2, 3])
lock(m) do
    @ref_into :mut arr2 = m[]
    push!(arr2, 4)
end
```

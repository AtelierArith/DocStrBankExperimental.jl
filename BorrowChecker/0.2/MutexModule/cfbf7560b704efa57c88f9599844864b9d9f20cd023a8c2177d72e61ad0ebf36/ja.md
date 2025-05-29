```
Mutex{T} <: AbstractMutex{T}
```

型Tの値を保護するミューテックス。保護された値への安全な同時アクセスを提供します。

# 例

```julia
m = Mutex([1, 2, 3])
lock(m)
@ref_into :mut arr = m[]
push!(arr, 4)
unlock(m)
```

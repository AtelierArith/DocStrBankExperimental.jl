```
solve!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}, iteration::Int; interpolationorder::Int=1)
```

`MDBM_Problem`を`iteration`回洗練させた後、隣接チェックを行います。`interpolationorder`はn-キューブ内の補間方法を定義します。

# 例

```julia
julia> solve!(mymdbm,4)
```

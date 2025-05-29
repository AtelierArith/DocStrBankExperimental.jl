```
pmap(fn::Function, o::Union{Array{PyObject}, PyObject})
```

並列forループ。異なる反復間にデータ依存性は存在しない必要があります。

# 例

```julia
x = constant(ones(10))
y1 = pmap(x->2.0*x, x)
y2 = pmap(x->x[1]+x[2], [x,x])
y3 = pmap(1:10, x) do z
    i = z[1]
    xi = z[2]
    xi + cast(Float64, i)
end
run(sess, y1)
run(sess, y2)
run(sess, y3)
```

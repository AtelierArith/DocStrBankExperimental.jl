```
lineview(sess::PyObject, pl::PyObject, loss::PyObject, θ1, θ2=nothing; n::Integer = 10)
```

関数をプロットします 

$$
h(α) = f((1-α)θ_1 + αθ_2)
$$

# 例

```julia
pl = placeholder(Float64, shape=[2])
l = sum(pl^2-pl*0.1)
sess = Session(); init(sess)
lineview(sess, pl, l, rand(2))
```

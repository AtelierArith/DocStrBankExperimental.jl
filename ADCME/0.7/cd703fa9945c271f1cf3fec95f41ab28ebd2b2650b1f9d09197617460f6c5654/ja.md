```
hessian(ys::PyObject, xs::PyObject; kwargs...)
```

`hessian` はスカラー関数 f のヘッセ行列をベクトル入力 xs に関して計算します。

# 例

```julia
x = constant(rand(10))
y = 0.5 * sum(x^2)
o = hessian(y, x)

sess = Session(); init(sess)
run(sess, o) # 単位行列であるべき
```

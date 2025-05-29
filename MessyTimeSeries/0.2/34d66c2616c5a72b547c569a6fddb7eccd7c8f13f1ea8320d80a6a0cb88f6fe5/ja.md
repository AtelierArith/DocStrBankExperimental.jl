```
solve_discrete_lyapunov(A::AbstractArray{Float64,2}, Q::SymMatrix)
```

双線形変換を使用して離散リャプノフ方程式を連続リャプノフ方程式に変換し、その後BLASを使用して解決します。

離散リャプノフ方程式を表すために使用される表記は

$$
P - APA' = Q
$$

,

であり、ここで$P$と$Q$は対称です。この方程式は次のように変換されます。

$$
B'P + PB = -C
$$

# 参考文献

Kailath (1980, page 180) ```

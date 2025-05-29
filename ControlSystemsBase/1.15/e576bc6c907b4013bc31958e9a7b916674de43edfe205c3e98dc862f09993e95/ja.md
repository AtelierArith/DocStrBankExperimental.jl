```
Qc = d2c(sys::AbstractStateSpace{<:Discrete}, Qd::AbstractMatrix; opt=:o)
```

`sys` に属する離散時間共分散行列を同等の連続時間行列に再サンプリングします。

使用される方法は、以下の参考文献の定理 5 に基づいています。

`opt = :c` の場合、行列は LQR 問題のコスト行列であると見なされます。

参考文献: Discrete-time Solutions to the Continuous-time Differential Lyapunov Equation With Applications to Kalman Filtering Patrik Axelsson and Fredrik Gustafsson

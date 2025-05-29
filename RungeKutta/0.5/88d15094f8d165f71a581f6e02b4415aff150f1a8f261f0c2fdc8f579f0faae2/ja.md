Runge-Kutta法のタブローを保持します

$$
\begin{aligned}
Q_{n,i} &= q_{n} + h \sum \limits_{j=1}^{s} a_{ij} \, v(t_{n} + c_j \Delta t, Q_{n,j}) , &
q_{n+1} &= q_{n} + h \sum \limits_{i=1}^{s} b_{i}  \, v(t_{n} + c_j \Delta t, Q_{n,i}) , \\
\end{aligned}
$$

パラメータ:

  * `T`: コエフィシエント配列のデータ型

フィールド:

  * `name`: タブローの記号名
  * `o`: メソッドの次数
  * `s`: ステージの数
  * `a`: コエフィシエント $a_{ij}$ で $ 1 \le i,j \le s$
  * `b`: 重み $b_{i}$ で $ 1 \le i \le s$
  * `c`: ノード $c_{i}$ で $ 1 \le i \le s$
  * `R∞`: 無限大での安定性関数

コンストラクタ:

```julia
Tableau{T}(name, o, s, a, b, c)
Tableau{T}(name, o, a, b, c)
Tableau(name::Symbol, o::Int, s::Int, a::AbstractMatrix, b::AbstractVector, c::AbstractVector)
Tableau(name::Symbol, o::Int, a::AbstractMatrix, b::AbstractVector, c::AbstractVector)
Tableau(name::Symbol, o::Int, t::AbstractMatrix)
```

最後のコンストラクタは、全体のタブローをバッチャータブローの形で保持する $(s+1) \times (s+1)$ 配列を受け入れます。すなわち、

|   c |   a |
| ---:| ---:|
|     |   b |

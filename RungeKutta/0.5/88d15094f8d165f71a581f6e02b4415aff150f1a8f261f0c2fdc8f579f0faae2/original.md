Holds the tableau of a Runge-Kutta method

$$
\begin{aligned}
Q_{n,i} &= q_{n} + h \sum \limits_{j=1}^{s} a_{ij} \, v(t_{n} + c_j \Delta t, Q_{n,j}) , &
q_{n+1} &= q_{n} + h \sum \limits_{i=1}^{s} b_{i}  \, v(t_{n} + c_j \Delta t, Q_{n,i}) , \\
\end{aligned}
$$

Parameters:

  * `T`: datatype of coefficient arrays

Fields:

  * `name`: symbolic name of the tableau
  * `o`: order of the method
  * `s`: number of stages
  * `a`: coefficients $a_{ij}$ with $ 1 \le i,j \le s$
  * `b`: weights $b_{i}$  with $ 1 \le i \le s$
  * `c`: nodes $c_{i}$  with $ 1 \le i \le s$
  * `R∞`: stability function at infinity

Constructors:

```julia
Tableau{T}(name, o, s, a, b, c)
Tableau{T}(name, o, a, b, c)
Tableau(name::Symbol, o::Int, s::Int, a::AbstractMatrix, b::AbstractVector, c::AbstractVector)
Tableau(name::Symbol, o::Int, a::AbstractMatrix, b::AbstractVector, c::AbstractVector)
Tableau(name::Symbol, o::Int, t::AbstractMatrix)
```

The last constructor accepts an $(s+1) \times (s+1)$ array that holds the whole tableau in the form of a Butcher tableau, i.e.,

|   c |   a |
| ---:| ---:|
|     |   b |

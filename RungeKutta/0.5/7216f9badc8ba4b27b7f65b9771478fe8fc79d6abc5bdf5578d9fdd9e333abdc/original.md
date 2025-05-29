Tableau of a Partitioned Runge-Kutta method

$$
\begin{aligned}
Q_{n,i} &= q_{n} + h \sum \limits_{j=1}^{s} a_{ij} \, v(t_{n} + c_j \Delta t, Q_{n,j}, P_{n,j}) , &
q_{n+1} &= q_{n} + h \sum \limits_{i=1}^{s} b_{i}  \, v(t_{n} + c_j \Delta t, Q_{n,i}, P_{n,i}) , \\
P_{n,i} &= p_{n} + h  \sum \limits_{i=1}^{s} \bar{a}_{ij} \, f(t_{n} + c_j \Delta t, Q_{n,j}, P_{n,j}) , &
p_{n+1} &= p_{n} + h \sum \limits_{i=1}^{s} \bar{b}_{i}   \, f(t_{n} + c_j \Delta t, Q_{n,i}, P_{n,i}) .
\end{aligned}
$$

Parameters:

  * `T`: datatype of coefficient arrays

Fields:

  * `name`: symbolic name of the tableau
  * `o`: order of the method
  * `s`: number of stages
  * `q`: Tableau for `q`
  * `p`: Tableau for `p`
  * `R∞`: stability function at infinity

The actual tableaus are stored in `q` and `p`:

  * `a`: coefficients $a_{ij}$ with $ 1 \le i,j \le s$
  * `b`: weights $b_{i}$  with $ 1 \le i \le s$
  * `c`: nodes $c_{i}$  with $ 1 \le i \le s$

Constructors:

```julia
PartitionedTableau{T}(name, o, q, p)
PartitionedTableau{T}(name, q, p)
PartitionedTableau(name::Symbol, q::Tableau, p::Tableau)
PartitionedTableau(name::Symbol, q::Tableau)
```

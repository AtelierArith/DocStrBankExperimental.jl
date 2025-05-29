`OrthPolyBasis1D3T:` は、3項再帰に基づいて多項式の基底を定義します。

$$
\begin{aligned}
   P_1(x) &= A_1  \\
   P_2 &= A_2 x + B_2 \\
   P_{n} &= (A_n x + B_n) P_{n-1}(x) + C_n P_{n-2}(x)
\end{aligned}
$$

通常（必ずしもそうではありませんが）、このような基底は、ユーザーが指定した分布に対してモノミアルを直交化することによって得られます。この分布は連続的または離散的である可能性がありますが、密度関数を持っている必要があります。次も参照してください。

  * `legendre_basis`
  * `chebyshev_basis`
  * `jacobi_basis`

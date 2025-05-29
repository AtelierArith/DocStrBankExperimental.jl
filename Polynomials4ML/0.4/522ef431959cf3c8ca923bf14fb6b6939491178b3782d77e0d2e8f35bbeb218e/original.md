`OrthPolyBasis1D3T:` defines a basis of polynomials in terms of a 3-term recursion, 

$$
\begin{aligned}
   P_1(x) &= A_1  \\
   P_2 &= A_2 x + B_2 \\
   P_{n} &= (A_n x + B_n) P_{n-1}(x) + C_n P_{n-2}(x)
\end{aligned}
$$

Typically (but not necessarily) such bases are obtained by orthogonalizing the monomials with respect to a user-specified distribution, which can be either continuous or discrete but must have a density function. See also 

  * `legendre_basis`
  * `chebyshev_basis`
  * `jacobi_basis`

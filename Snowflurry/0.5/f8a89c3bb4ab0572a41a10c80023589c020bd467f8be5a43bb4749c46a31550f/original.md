A `Ket` represents a *quantum wavefunction* and is mathematically equivalent to a column vector of complex values. The norm of a Ket should always be unity.   A `Ket` representing a system with a qubit count of $n=2$ has $2^n$ states.  By convention, qubit 1 is the leftmost bit, followed by every subsequent qubit.  Hence, a 2-qubit `Ket` has 4 complex-valued coefficients $a_{ij}$, each corresponding to state $\left|ij\right\rangle$, in the following order:

$$
\psi = \begin{bmatrix}
    a_{00}  \\
    a_{10}  \\
    a_{01}  \\
    a_{11}  \\
    \end{bmatrix}.
$$

# Examples

A Ket can be initialized by using a pre-built basis such as the `fock` basis. See [`fock`](@ref) for further information on this function. 

```jldoctest
julia> ψ = fock(2, 4)
4-element Ket{ComplexF64}:
0.0 + 0.0im
0.0 + 0.0im
1.0 + 0.0im
0.0 + 0.0im


```

Although NOT the preferred way, one can also directly build a Ket object by passing a column vector as the initializer. 

```jldoctest
julia> using Snowflurry

julia> ψ = Ket([1.0; 0.0; 0.0; 0.0])
4-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.0 + 0.0im


```

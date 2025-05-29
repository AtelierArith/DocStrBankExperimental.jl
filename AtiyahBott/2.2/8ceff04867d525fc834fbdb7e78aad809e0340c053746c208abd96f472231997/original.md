```
Psi(a)
```

Equivariant class of the cycle of $\psi$-classes.

# Arguments

  * `a::Vector{Int64}`: the vector of the exponents of the $\psi$ classes. It is ordered, meaning that the first element is the exponent of $\psi_1$, the second is the exponent of $\psi_2$, and so on.

!!! note
    The size of `a` must be at most `m`. If it is smaller, missing exponents will be considered as zeros. If `a` is a number, it will be considered as the exponent of $\psi_1$.


!!! warning "Attention!"
    The program will stop if we have one of the following conditions:

      * the size of `a` is bigger than `m`,
      * `a` contains a negative number.


# Example

The following Gromov-Witten invariants

$$
\begin{aligned}
\int_{\overline{M}_{0,2}(\mathbb{P}^{6},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{6}}(1)^{5}\cdot\mathrm{ev}_{2}^{*}\mathcal{O}_{\mathbb{P}^{6}}(1)^{2}\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{6}}(5)))\cdot\psi_{1}\psi_{2}^{0} &= 495000 \\
\int_{\overline{M}_{0,2}(\mathbb{P}^{10},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{10}}(1)^{8}\cdot\mathrm{ev}_{2}^{*}\mathcal{O}_{\mathbb{P}^{10}}(1)^{6}\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{10}}(7)))\cdot\psi_{1}^{2} &= 71804533752 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{2},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2}\cdot\psi_{1}^{4} &= \frac{1}{8} \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{2},2)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2})^{4}\cdot\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)\cdot(\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)+\psi_{1}) &= 2 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{3},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)\cdot(\psi_{1}^{7}\cdot\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)+\psi_{1}^{6}\cdot\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2}) &= -\frac{5}{16} \\
\end{aligned}
$$

can be computed as

```jldoctest; setup = :(using AtiyahBott)
julia> P = O1_i(1)^5*O1_i(2)^2*Hypersurface(5)*Psi([1,0]);

julia> AtiyahBottFormula(6, 2, 2, P, show_bar=false);
Result: 495000

julia> P = O1_i(1)^8*O1_i(2)^6*Hypersurface(7)*Psi(2);

julia> AtiyahBottFormula(10, 2, 2, P, show_bar=false);
Result: 71804533752

julia> P = O1()^2*Psi(4);

julia> AtiyahBottFormula(2, 2, 1, P, show_bar=false);
Result: 1//8

julia> P = Incidency(2)^4*O1_i(1)*(O1_i(1) + Psi(1));

julia> AtiyahBottFormula(2, 2, 1, P, show_bar=false); #number of plane conics through four points and tangent to a line
Result: 2

julia> P = O1()*(Psi(7)*O1()+Psi(6)*O1()^2);

julia> AtiyahBottFormula(3, 2, 1, P, show_bar=false);
Result: -5//16
```

!!! warning "Psi is singleton!"
    `Psi` cannot be multiplied by itself.

    ```julia-repl
    julia> P = O1()^2*Psi(1)^4;                  #this is **wrong**
    julia> AtiyahBottFormula(2,2,1,P);
    Warning: more instances of Psi has been found. Type:
    julia> ?Psi
    for support.
    julia> P = O1()^2*Psi(3)*Psi(1);             #this is **wrong**
    julia> AtiyahBottFormula(2,2,1,P);
    Warning: more instances of Psi has been found. Type:
    julia> ?Psi
    for support.
    julia> P = O1()^2*Psi(4);
    julia> AtiyahBottFormula(2,2,1,P);
    Result: 1//8
    ```


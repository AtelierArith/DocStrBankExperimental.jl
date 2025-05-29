```
ArchimaxCopula{A, E}
```

Fields:

```
-Archimedean::A - Archimedean Copula
-Extreme::E - Extreme Value Copula
```

Constructor

```
ArchimaxCopula(Archimedean, Extreme)
```

The bivariate Archimax Copula is parameterized by an Archimedean Copula and Extreme Value Copula. It is constructed as follows: 

$$
C_{\ell, \varphi}(u_1, u_2) = \varphi(\ell(\varphi^{-1}(u_1),\varphi^{-1}(u_2)))
$$

where $\varphi$ is the generator of the Archimedean Copula and $\varphi^{-1}$ is the inverse and $\ell$ is the stable tail dependece function of Extreme value Copula

For more details see

References:

  * [Charpentier2014](@cite) Charpentier et al, Multivariate Archimax Copulas, Journal of Multivariate analysis. 2014.

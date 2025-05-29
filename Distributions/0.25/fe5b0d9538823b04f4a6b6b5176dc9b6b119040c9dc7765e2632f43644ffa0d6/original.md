```
Dirichlet
```

The [Dirichlet distribution](http://en.wikipedia.org/wiki/Dirichlet_distribution) is often used as the conjugate prior for Categorical or Multinomial distributions. The probability density function of a Dirichlet distribution with parameter $\alpha = (\alpha_1, \ldots, \alpha_k)$ is:

$$
f(x; \alpha) = \frac{1}{B(\alpha)} \prod_{i=1}^k x_i^{\alpha_i - 1}, \quad \text{ with }
B(\alpha) = \frac{\prod_{i=1}^k \Gamma(\alpha_i)}{\Gamma \left( \sum_{i=1}^k \alpha_i \right)},
\quad x_1 + \cdots + x_k = 1
$$

```julia
# Let alpha be a vector
Dirichlet(alpha)         # Dirichlet distribution with parameter vector alpha

# Let a be a positive scalar
Dirichlet(k, a)          # Dirichlet distribution with parameter a * ones(k)
```

The [Multinomial distribution](http://en.wikipedia.org/wiki/Multinomial_distribution) generalizes the *binomial distribution*. Consider n independent draws from a Categorical distribution over a finite set of size k, and let $X = (X_1, ..., X_k)$ where $X_i$ represents the number of times the element $i$ occurs, then the distribution of $X$ is a multinomial distribution. Each sample of a multinomial distribution is a k-dimensional integer vector that sums to n.

The probability mass function is given by

$$
f(x; n, p) = \frac{n!}{x_1! \cdots x_k!} \prod_{i=1}^k p_i^{x_i},
\quad x_1 + \cdots + x_k = n
$$

```julia
Multinomial(n, p)   # Multinomial distribution for n trials with probability vector p
Multinomial(n, k)   # Multinomial distribution for n trials with equal probabilities
                    # over 1:k
```

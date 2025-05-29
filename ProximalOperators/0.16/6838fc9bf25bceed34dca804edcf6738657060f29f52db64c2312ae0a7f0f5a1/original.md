```
Precompose(f, L, μ, b)
```

Return the function

$$
g(x) = f(Lx + b)
$$

where $f$ is a convex function and $L$ is a linear mapping: this must satisfy $LL^* = μI$ for $μ > 0$. Furthermore, either $f$ is separable or parameter `μ` is a scalar, for the `prox` of $g$ to be computable.

Parameter `L` defines $L$ through the `mul!` method. Therefore `L` can be an `AbstractMatrix` for example, but not necessarily.

In this case, `prox` and `prox!` are computed according to Prop. 24.14 in Bauschke, Combettes "Convex Analysis and Monotone Operator Theory in Hilbert Spaces", 2nd edition, 2016. The same result is Prop. 23.32 in the 1st edition of the same book.

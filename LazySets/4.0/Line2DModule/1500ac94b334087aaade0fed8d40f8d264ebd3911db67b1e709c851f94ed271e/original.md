# Extended help

```
an_element(L::Line2D)
```

### Algorithm

The algorithm is a 2D specialization of the `Hyperplane` algorithm.

If the $b$ value of the line is zero, the result is the origin. Otherwise the result is some $x = (x_1, x_2)ᵀ$ such that $a·x = b$. We first find out the dimension $i$ in which $a = (a_1, a_2)ᵀ$ is nonzero and then choose $x_i = \frac{b}{a_i}$ and $x_{3-i} = 0$.

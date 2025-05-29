```
  simplest_between(l::QQFieldElem, r::QQFieldElem)
```

Return the simplest fraction in the closed interval $[l, r]$. A canonical fraction $a_1 / b_1$ is defined to be simpler than $a_2 / b_2$ if and only if $b_1 < b_2$ or $b_1 = b_2$ and $a_1 < a_2$.

# Examples

```jldoctest
julia> simplest_between(QQ(1//10), QQ(3//10))
1//4
```

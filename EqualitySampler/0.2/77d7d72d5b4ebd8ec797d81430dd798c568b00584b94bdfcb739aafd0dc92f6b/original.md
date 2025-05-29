```julia
count_equalities(urns::AbstractArray{T<:Integer, 1}) -> Any

```

Count the number of equality constraints implied by a partition. This assumes some elegant ordering of the constraints. For example the partition $\{\{\theta_1, \theta_3\}, \{\theta_2\}\}$ can be written as $\theta_1 = \theta_3 \neq \theta_2$ and therefore `count_equalities([1, 2, 1]) == 1`.

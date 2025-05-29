```
random_configuration_model(n, ks)
```

Create a random undirected graph according to the [configuration model](http://tuvalu.santafe.edu/~aaronc/courses/5352/fall2013/csci5352_2013_L11.pdf) containing `n` vertices, with each node `i` having degree `k[i]`.

### Optional Arguments

  * `seed=-1`: set the RNG seed.
  * `check_graphical=false`: if true, ensure that `k` is a graphical sequence

(see [`isgraphical`](@ref)).

### Performance

Time complexity is approximately $\mathcal{O}(n \bar{k}^2)$.

### Implementation Notes

Allocates an array of $n \bar{k}$ `Int`s.

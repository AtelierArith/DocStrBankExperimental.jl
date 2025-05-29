```
random_configuration_model(n::Int, k::Vector{Int}, G=Graph; seed=-1, check_graphical=false)
```

Creates a random undirected graph according to the [configuration model](http://tuvalu.santafe.edu/~aaronc/courses/5352/fall2013/csci5352_2013_L11.pdf). It contains `n` vertices, the vertex `i` having degree `k[i]`.

Defining `c = mean(k)`, it allocates an array of `nc` `Int`s, and takes approximately $nc^2$ time.

If `check_graphical=true` makes sure that `k` is a graphical sequence (see `is_graphical`).

`G` is the resulting graph type.

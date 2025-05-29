# DAG

Directed acyclic graph constructor

```julia
DAG(name, model; df)

```

### Required arguments

```julia
* `name::AbstractString`               : Name for the DAG object
* `d::ModelDefinition`                 : DAG definition
```

where

```
ModelDefinition = Union{OrderedDict, AbstractString, NamedArray}
```

See the extended help for a usage example.

### Keyword arguments

```julia
* `df::DataFrame`                      : DataFrame with observations
```

### Returns

```julia
* `dag::DAG`                           : Boolean result of test
```

# Extended help

In the definition of the OrderedDict, read `=>` as `~` in regression models or `<-` in causal models, e.g.:

```julia
d = OrderedDict(
  :u => [:x, :v],
  :s1 => [:u],
  :w => [:v, :y],
  :s2 => [:w]
);
dag = DAG("my_name", d)
```

Coming from R's dagitty:

amat <- dagitty("dag { {X V} -> U; S1 <- U; {Y V} -> W; S2 <- W}”)

```julia
dag = DAG("my_name", "dag { {X V} -> U; S1 <- U; {Y V} -> W; S2 <- W}”)
display(dag) # Show the DAG
```

Coming from R's ggm:

amat <- DAG(U~X+V, S1~U, W~V+Y, S2~W, order=FALSE)

```julia
dag = DAG("my_name", "DAG(U~X+V, S1~U, W~V+Y, S2~W”)
display(dag) # Show the DAG
```

### Acknowledgements

Original author:                       Giovanni M. Marchetti

Translated to Julia:                   Rob J Goedman

### License

The R package ggm is licensed under License: GPL-2.

The Julia translation is licenced under: MIT.

Part of API, exported.

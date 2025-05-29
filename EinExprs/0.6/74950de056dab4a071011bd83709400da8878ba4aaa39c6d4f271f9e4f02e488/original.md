```
suminds(path)
```

Indices of summation of an `EinExpr`.

$$
\mathtt{path} \equiv \sum_{j k l m n o p} A_{mi} B_{ijp} C_{jkn} D_{pkl} E_{mno} F_{ol}
$$

```julia
suminds(path) == [:j, :k, :l, :m, :n, :o, :p]
```

```
suminds(path)
```

`EinExpr`の総和のインデックス。

$$
\mathtt{path} \equiv \sum_{j k l m n o p} A_{mi} B_{ijp} C_{jkn} D_{pkl} E_{mno} F_{ol}
$$

```julia
suminds(path) == [:j, :k, :l, :m, :n, :o, :p]
```

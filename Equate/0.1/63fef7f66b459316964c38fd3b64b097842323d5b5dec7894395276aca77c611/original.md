```
ChainedEquipercentile(X::NEAT, Y::NEAT; case = :middle)
```

# Algorithm

Chained equipercentile equating is, in short, to conduct equipercentile equating consecutively. First, find equipercentile relationship for score X to scores V on the first population. This function is referred to as 𝑒V1(𝑥). Second, fubd the equipercentile relationship for converting scores on the common items(V) to scores on the form Y based on examinees from the population 2. Refer to the resulting function as 𝑒Y2(𝑣).

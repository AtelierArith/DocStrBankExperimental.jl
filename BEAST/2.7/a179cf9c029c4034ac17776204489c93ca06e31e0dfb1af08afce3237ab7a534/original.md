```
discr(eq, pairs...)
```

This macro provides syntactical sugar for the definition of a discretisation of a varational formulation. Given a variational equation EQ: Find j ∈ X such that for all k ∈ Y a(k,j) = f(k) can be discretised by stating:

```
eq = @discretise EQ j∈X k∈Y
```

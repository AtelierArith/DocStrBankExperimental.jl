```
EoSVirial2 <: SecondVirialModel
EoSVirial2(model;idealmodel = idealmodel(model))
```

## Input models

  * `model`: Model providing second virial coefficient is obtained
  * `idealmodel`: Ideal Model

## Description

Virial model, that just calls the second virial coefficient of the underlying model.

```
B(T,z) = B(model,T,z)
```

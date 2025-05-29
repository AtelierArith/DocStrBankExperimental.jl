```
formulation(i::CombinatorialInstance, f::CombinatorialLinearFormulation)
```

Returns the LP formulation `f` for this combinatorial instance. It returns  two arguments: 

  * the JuMP model
  * the decision variables

For `CombinatorialVariation`, it also returns a third argument: the  supplementary constraint encoded by the `CombinatorialVariation` on top fo the  `CombinatorialInstance`.

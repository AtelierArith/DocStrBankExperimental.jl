```
multiverse = @enter begin
    @choose x = 1:5
    y = 2 * x + 3
    @measure z = sqrt(y)
end
```

Prepare a multiverse analysis based on the provided block of code.

Choices are denoted by the `@choose` macrocall and must assign a collection to a variable. Measurements are denoted by the `@measure` macrocall and must assign a value to a variable.

The multiverse can have the measurements in each choice-set universe populated using the `explore!` method, either all at once or iteratively.

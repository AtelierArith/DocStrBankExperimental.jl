A function that maintains a state (initially s0) and has monadic output for some  polynomial monad t.

The function f must be of type S × WireVal → S × (t ◁ WireVal) 

```
                            (i.e. S × Wireval → MealyRes)
```

Generate a comparison of cumulative costs for a range of learning rates (0 to 1)  across the three methods: Wright, Crawford, and Experience.

```
learn_rates(InitialEffort, Units; LC_Step=0.1)
```

Returns a DataFrame with columns:

  * `LC`: The learning rate.
  * `Wright`: Cumulative cost from Wright's model.
  * `Crawford`: Cumulative cost from Crawford's model.
  * `Experience`: Cumulative cost from the Experience model.

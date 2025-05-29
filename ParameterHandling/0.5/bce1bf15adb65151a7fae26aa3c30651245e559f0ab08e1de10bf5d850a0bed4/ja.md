```
bounded(val::Real, lower_bound::Real, upper_bound::Real)
```

`Bounded`を構築します。`Bounded`の`value`は、`Real`数であり、区間（`lower_bound`、`upper_bound`）内に制約され、`val`に等しくなります。これは、内部的には`unconstrained_value`と、この区間に任意の`Real`をマッピングする`transform`の観点から表現されます。

```
ccdf(prior::Distribution, Z::EBayesSample)
```

Given a `prior` $G$ and `EBayesSample` $Z$, evaluate the complementary CDF of the marginal distribution of $Z$ at `response(Z)`.

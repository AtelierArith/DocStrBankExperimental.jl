```
AbstractEffectSize
```

An abstract type to represent an effect size.

| Effect | Effect size |
|:------ | -----------:|
| Small  |         0.2 |
| Medium |         0.5 |
| Large  |         0.8 |

Subtypes implement:

| Method       | Description                     |
|:------------ |:------------------------------- |
| `effectsize` | returns the effect size index   |
| `confint`    | returns the confidence interval |

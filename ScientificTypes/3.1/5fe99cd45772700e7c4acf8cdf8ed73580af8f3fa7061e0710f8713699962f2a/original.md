```
schema(X)
```

Inspect the column types and scitypes of a tabular object. returns `nothing` if the column types and/or scitypes can't be inspected.

## Example

```
X = (ncalls=[1, 2, 4], mean_delay=[2.0, 5.7, 6.0])
schema(X)
```

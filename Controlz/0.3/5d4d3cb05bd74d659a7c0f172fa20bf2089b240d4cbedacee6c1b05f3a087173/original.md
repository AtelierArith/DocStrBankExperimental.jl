```
evaluate(tf, z)
```

evaluate a `TransferFunction`, `tf`, at a particular number `z` (could be complex).

# example

```jldoctest eval
tf = TransferFunction([1], [3, 1])
evaluate(tf, 1.0)
# output
0.25
```

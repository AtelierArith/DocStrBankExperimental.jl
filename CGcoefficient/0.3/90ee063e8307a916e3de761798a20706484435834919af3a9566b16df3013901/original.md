```
binomial_data_size(n::Int)::Int
```

Store (half) binomial data in the order of

```text
# n - data
  0   1
  1   1
  2   1 2
  3   1 3
  4   1 4 6
  5   1 5 10
  6   1 6 15 20
```

Return the total number of the stored data.

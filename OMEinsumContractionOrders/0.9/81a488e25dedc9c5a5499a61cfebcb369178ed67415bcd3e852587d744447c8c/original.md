```
contraction_complexity(eincode, size_dict) -> ContractionComplexity
```

Returns the time, space and read-write complexity of the einsum contraction. The returned object contains 3 fields:

  * time complexity `tc` defined as `log2(number of element-wise multiplications)`.
  * space complexity `sc` defined as `log2(size of the maximum intermediate tensor)`.
  * read-write complexity `rwc` defined as `log2(the number of read-write operations)`.

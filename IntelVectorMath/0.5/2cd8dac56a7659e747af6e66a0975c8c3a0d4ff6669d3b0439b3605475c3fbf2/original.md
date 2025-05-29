```
VML_DENORMAL_FAST :: VMLFastDenormal
```

Designed to improve the performance of computations that involve denormalized numbers at the cost of reasonable accuracy loss. This mode changes the numeric behavior of the functions: denormalized input values are treated as zeros and denormalized results are flushed to zero. Accuracy loss may occur if input and/or output values are close to denormal range.

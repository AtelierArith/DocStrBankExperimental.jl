```
dense(::MPS/MPO)
```

Given an MPS (or MPO), return a new MPS (or MPO) having called `dense` on each ITensor to convert each tensor to use dense storage and remove any QN or other sparse structure information, if it is not dense already.

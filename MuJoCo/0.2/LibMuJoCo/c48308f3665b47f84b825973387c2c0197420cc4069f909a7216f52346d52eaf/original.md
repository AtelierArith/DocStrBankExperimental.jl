```
mj_freeStack(d)
```

Free the current mjData stack frame. All pointers returned by mj*stackAlloc since the last call to mj*markStack must no longer be used afterwards.

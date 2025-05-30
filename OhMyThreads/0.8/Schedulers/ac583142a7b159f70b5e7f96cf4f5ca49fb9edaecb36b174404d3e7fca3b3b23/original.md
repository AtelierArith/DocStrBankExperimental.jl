```
SerialScheduler (aka :serial)
```

A scheduler for turning off any multithreading and running the code in serial. It aims to make parallel functions like, e.g., `tmapreduce(sin, +, 1:100)` behave like their serial counterparts, e.g., `mapreduce(sin, +, 1:100)`.

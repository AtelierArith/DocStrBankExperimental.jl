```
XPRS_CALLBACKFROMMASTERTHREAD
```

Branch and Bound: specifies whether the MIP callbacks should only be called on the master thread. (integer)

Default value: `0`

Values: 0 : Invoke callbacks on worker threads during parallel MIP; 1 : Only ever invoke a callback on the thread that called `XPRSmipoptimize`.

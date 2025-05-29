```
off(obsfunc::ObserverFunction)
```

Remove the listener function `obsfunc.f` from the listeners of `obsfunc.observable`. Once `obsfunc` goes out of scope, this should allow `obsfunc.f` and all the values it might have closed over to be garbage collected (unless there are other references to it).

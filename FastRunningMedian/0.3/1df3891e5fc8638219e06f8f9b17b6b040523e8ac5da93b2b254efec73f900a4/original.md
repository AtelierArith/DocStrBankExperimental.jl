```
roll!(mf::MedianFilter, val) -> mf
```

Roll the window over to the next position by replacing the first and oldest element in the ciruclar buffer with the new value `val`. 

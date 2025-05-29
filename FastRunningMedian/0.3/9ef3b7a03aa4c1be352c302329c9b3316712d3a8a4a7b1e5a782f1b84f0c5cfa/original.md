```
shrink!(mf::MedianFilter) -> mf
```

Shrinks `mf` by removing the first and oldest element in the circular buffer. 

Will error if mf contains only one element as a MedianFilter with zero elements would not have a median. 

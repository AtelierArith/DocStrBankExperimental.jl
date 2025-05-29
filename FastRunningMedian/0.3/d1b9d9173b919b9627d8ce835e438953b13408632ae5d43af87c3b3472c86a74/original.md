```
median(mf::MedianFilter; nan=:include)
```

Determine the current median in `mf`. 

## NaN Handling

By default, any NaN value in the filter will turn the result NaN.

Use the keyword argument `nan = :ignore` to ignore NaN values and calculate the median  over the remaining values. If there are only NaNs, the median will be NaN regardless. 

## Implementation

If the number of elements in MedianFilter is odd, the low_heap is always one element bigger than the high_heap. The top element of the low_heap then is the median. 

If the number of elements in MedianFilter is even, both heaps are the same size and the median is the mean of both top elements. 

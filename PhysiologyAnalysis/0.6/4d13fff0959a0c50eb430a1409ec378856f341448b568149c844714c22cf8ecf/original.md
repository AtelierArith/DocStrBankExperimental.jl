```
calculate_threshold(vm_arr::AbstractArray; Z = 4, dims = -1)
```

Finds the threshold of a trace by calculating the average and then adding the 4x the standard deviation.  If using a differential solution, make sure dt is set, otherwise the standard deviation will be unevenly sampled

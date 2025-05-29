```
Windows3(y, t, v, n=length(y)÷8, noverlap=-1, window_func=rect)
```

noverlap = -1 sets the noverlap to n/2

#Arguments:

  * `y`: Signal
  * `t`: Time vector
  * `v`: Auxiliary vector
  * `n`: Number of datapoints per window
  * `noverlap`: Overlap between windows
  * `window_func`: Function to apply over window

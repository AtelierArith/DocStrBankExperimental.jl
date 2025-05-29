```
detrend(t, y, order = 1, bp = [])
```

Detrend a signal `y` with respect to time `t` using a polynomial of order `order`.

**Inputs**

  * `t`: Time vector
  * `y`: Signal to be detrended
  * `order`: Order of the polynomial (default is 1)
  * `bp`: Breakpoints for the polynomial (default is empty)

**Output**

  * `y_detrended`: Detrended signal

**Notes**

`order` can be a vector if the trend is different over the segments defined by the breakpoints `bp`.

The breakpoints `bp` are the points where the polynomial order changes. If `bp` is empty, a single polynomial is fitted to the entire signal.

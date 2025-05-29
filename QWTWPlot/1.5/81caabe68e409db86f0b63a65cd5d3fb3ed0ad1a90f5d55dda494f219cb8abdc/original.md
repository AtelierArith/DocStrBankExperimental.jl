```
qfigure(n::Integer = 0; xAxisType=:aLinear, yAxisType=:aLinear)::Int32
```

create a new plot window, OR make plot (with this ID 'n') 'active'.

looks like 'n' have to be an integer number (this plot ID, or zero if you do not care).
after this function, this plot is the "active plot". 
If 'n == 0' then another new plot will be created. xAxisType and yAxisType could be :aLinear (default) or :aLog (logarithmic)

Returns ID of the created plot. 

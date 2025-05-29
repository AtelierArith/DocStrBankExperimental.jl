```
make_yaxis(fig,ang::Number,max::Number,label::String,ticks::Tuple)
```

Plot an axis from scratch when you want the y-axis to have an <90° angle with respect to the x-axis.

# Inputs

  * `fig` : actual figure
  * `ang` : angle between y and x-axis (in radians)
  * `max` : maximum value of the axis
  * `label` : label of the axis
  * `ticks` : ticks of the axis (of the form Tuple : (ticks, tickslabels))

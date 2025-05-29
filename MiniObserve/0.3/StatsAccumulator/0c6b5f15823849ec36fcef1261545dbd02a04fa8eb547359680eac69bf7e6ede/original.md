Construct a histogram accumulator. 

Arguments:

  * `min` - minimum value [`T(0)`]
  * `width` - bin size [`T(1)`]
  * `max` - maximum value. Set lower than or equal to `min` to let the histogram adjust size automatically. [`min`]
  * `count_below_min` - whether values lower than `min` are ignored or counted in the first bin [`false`]
  * `count_above_max` - whether values larger than `max` are ignored or counted in the last bin [`false`]

add*volcano!(     Phases, Temp, Grid::CartData;     volcanic*phase,     center,     height,     radius,     crater,     base,     background,     T, )

Adds a volcano topography (cones and truncated cones)

# Parameters

  * Phases - Phase array (consistent with Grid)
  * Temp - Temperature array (consistent with Grid)
  * Grid - CartData

# Optional Parameters

  * volcanic_phase - phase number of the volcano,
  * center - x- and -coordinates of center of volcano
  * height - height of volcano
  * radius - radius of volcano
  * T - temperature structure of the volcano
  * crater - this will create a truncated cone and the option defines the radius of the flat top
  * base - this sets the flat topography around the volcano
  * background - this allows loading in a topography and only adding the volcano on top (also allows stacking of several cones to get a volcano with different slopes)

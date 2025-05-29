Interpolates in 1D or 2D using BSplineOrder(order=4) the x/y path.

# arguments

x: Vector of Numeric, or vector of Point2f [y: if x/y pairs are provided, will call the function on both axes individually]

# keyword

`winsize=4`: Over how many samples the interpolation function should run. For order =4, needs to be at least 4. For higher orders you need to increase this - you might get better interpolation by raising this, but i'm not sure. `subsample=5`: How many points to evaluate the spline on, effectively how many intermediate points to return. `order=4` the order of the BSPline. 4 is default, 2 is linear.

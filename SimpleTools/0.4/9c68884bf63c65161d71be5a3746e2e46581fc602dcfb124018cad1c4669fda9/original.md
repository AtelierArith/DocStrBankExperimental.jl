`make_continuous!(vals,mod)` assumes that the list of numbers in `vals` should represent a continuous stream of numbers, but with ambiguity modulo `mod`. For example, they are the angles of a continuous list of complex values, but there is an ambiguity modulo 2π. This function adjusts the values so they appear continuous.

For finer control, use `make_continuous!(vals,mod,thresh)` where `thresh` is the maximum allowable difference between consecutive entries in `val`.

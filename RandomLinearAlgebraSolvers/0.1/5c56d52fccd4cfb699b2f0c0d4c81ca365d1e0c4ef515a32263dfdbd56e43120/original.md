Randomized Kaczmarz

Section 3.3 in Gower, R. M., & Richtárik, P. (2015). Randomized iterative methods for linear systems. SIAM Journal on Matrix Analysis and Applications, 36(4), 1660-1690.

RK takes a step in the direction of the negative stochastic gradient. This means that it is equivalent to the SGD method. However, the stepsize choice is very special: RK chooses the stepsize which leads to the point which is closest to x* in the Euclidean norm.

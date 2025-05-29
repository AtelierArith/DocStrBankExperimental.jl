bnd(x::MC, lb, ub)

Sets the lower interval bound and the convex relaxation of `x` to a value of at least `lb`. Sets the upper interval bound and the concave relaxation of `x` to a value of at most `ub`. (Sub)gradients are adjusted appropriately.

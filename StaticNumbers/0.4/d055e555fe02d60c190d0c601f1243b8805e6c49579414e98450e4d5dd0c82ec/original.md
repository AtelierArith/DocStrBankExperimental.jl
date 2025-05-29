trystatic(x, y1, y2, ...) x ⩢ y1 ⩢ y2 ...

Test if a number `x` is equal to any of the numbers `y1`, `y2`, ..., and in that case return `static(y)`. Otherwise, or if `x` is already a `Static` number, `x is returned unchanged.

The inferred return type will typically be a small `Union`, which Julia can handle efficiently.

This function can be used to call specialized methods for certain input values. For example, `f(x, y ⩢ 0)` will call `f(x, y)` if `y` is nonzero, but `f(x, static(0))` if y is zero. This is useful if it enables optimizations that outweigh the cost of branching.

NOTE: When the list of y-values is longer than one, y1, y2, ... must be `Static` numbers, or inferrence will not work. (In which case `trystatic` is not more efficient than `static(x)`.)

A member function of a dictionary is evaluated using the `eval_element` routine. It takes as arguments the dictionary, the index of the member function and the point in which to evaluate.

This function performs bounds checking on the index and also checks whether the point x lies inside the support of the function. A `BoundsError` is thrown for an index out of bounds. The value `0` is returned when x is outside the support.

After the check on the index, the function calls `unsafe_eval_element1.` This function checks whether `x` lies in the support, and then calls `unsafe_eval_element`. The latter function should be implemented by a concrete dictionary. Any user who wants to avoid the bounds check or the support check can intercept `eval_element` or `unsafe_eval_element1` respectively.

" Make a weights vector which weights the matrix `data` so when summed the col totals sum to `target_populations` See the Creedy Paper for `function_type` If using one of the constrained types, the output weights should be no more than ru*the initial weight, no less than rl Returns a Dict with :=>weights and some extra info on convergence. data : KxJ matrix where k is num observations and J is num constraints; see: Microdata Adjustment by the Minimum Information Loss Principle Joachim Merz; FFB Discussion Paper No. 10 July 1994 for a good discussion on how to lay out the dataset

`data` :  `intial_weights` : K length vector `target_populations` - J length vector;

`upper_multiple` `lower_multiple` max/min acceptable values of ratio of final*weight/initial*weight (for constrained distance functions) `tol` for the root finder  `max_iterations` : for controlling convergence

note: chi-square is just there for checking purposes; use `do_chi_square_reweighting` if that's all you need.

upper*multiple/lower*multiple max/min acceptable values of ratio of final*weight/initial*weight (for constrained distance functions)

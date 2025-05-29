A categorical distribution, P(x|parents(x)) where all parents are discrete integers 1:N.

The ordering of `distributions` array follows the convention in Decision Making Under Uncertainty. Suppose a variable has three discrete parents. The first parental instantiation assigns all parents to their first bin. The second will assign the first parent (as defined in `parents`) to its second bin and the other parents to their first bin. The sequence continues until all parents are instantiated to their last bins.

This is equivalent to:

X,Y,Z 1,1,1 2,1,1 1,2,1 2,2,1 1,1,2 ...

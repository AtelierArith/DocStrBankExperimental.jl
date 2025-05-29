Usage: Intervals=PersistenceIntervals(FilteredComplex,maxdim,baseFileName);

This function computes Persistance intervals (over F*2) of a Filtered complex   The inputs are   (1) a filtered complex of type FiltrationOfSimplicialComplexes,   (2) an upper bound for the computation of considered dimensions H*k   (i.e. we only compute H_k for k less than or equal to maxdim)   The output is an array, whose ith entry is the (i-1)-dimensional persistence intervals.

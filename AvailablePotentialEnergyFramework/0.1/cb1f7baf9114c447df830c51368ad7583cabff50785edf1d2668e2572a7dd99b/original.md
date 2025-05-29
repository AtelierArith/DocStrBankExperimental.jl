smooth*and*mask!(buf,surf*pres*anomaly, threshold = -9)

Takes a 2d array and smooths it using a rolling median filter.  It then returns the elements of the filtered array whose values are less than the threshold.

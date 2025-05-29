Get the values of f which in direction dim have the hightest index where mask is true

fdeep = deepestpoint(mask,f,dim=ndims(f));

# Input:

  * mask: true for points to take into account.
  * f: array in which the points are taken
  * dim: along which dimension depth is found and integral is performed. If not provided last dimension is used

# Output:

  * values of f which in direction dim are found at the highest index not being false in the mask

# Note:

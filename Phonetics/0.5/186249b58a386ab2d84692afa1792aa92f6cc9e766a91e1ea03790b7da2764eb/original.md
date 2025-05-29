A vantage-point tree. Implemented from Samet, H. (2006). *Foundations of multidimensional and metric data structures*. San Francisco, California: Morgan Kaufmann. This data structure allows for searching a metric space in a more efficient way than comparing all points to each other. The "text" portion of the name is to imply that this tree will work with text-based data, and, in fact, is what it was tested to work with. In theory, however, it should work for numerical data as well.

# Parameters

  * **pivot** The pivot point chosen for the tree for a particular node; the   remaining data points will be assined to either the left or right tree based   on the median distance between them and this pivot point
  * **d** A distance function that will produce a similarity score between two   data points
  * **left** The left subtree containing all the points that are less than the   median distance away from $pivot$
  * **right** The right subtree containing all the points that are greater than or   equal to the median distance away from $pivot$

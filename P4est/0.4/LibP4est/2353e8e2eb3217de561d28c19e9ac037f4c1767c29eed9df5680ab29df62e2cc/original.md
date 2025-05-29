Callback function for the top-down search through the whole forest.

### Parameters

  * `p4est`:[in] The forest to search. We recurse through the trees one after another.
  * `which_tree`:[in] The current tree number.
  * `quadrant`:[in] The current quadrant in the recursion. This quadrant is either a non-leaf tree branch or a leaf. If the quadrant is contained in the local partition, we know which, otherwise we don't. Let us first consider the situation when **quadrant** is local, which is indicated by both **pfirst** and **plast** being equal to `p4est`->mpirank. Then the parameter **local_num** is negative for non-leaves and the number of the quadrant as a leaf in local storage otherwise. Only if the quadrant is a local leaf, it points to the actual local storage and can be used to access user data etc., and the recursion terminates. The other possibility is that **pfirst** < **plast**, in which case we proceed with the recursion, or both are equal to the same remote rank, in which case the recursion terminates. Either way, the quadrant is not from local forest storage.
  * `pfirst`:[in] The lowest processor that owns part of **quadrant**. Guaranteed to be non-empty.
  * `plast`:[in] The highest processor that owns part of **quadrant**. Guaranteed to be non-empty.
  * `local_num`:[in] If **quadrant** is a local leaf, this number is the index of the leaf in local quadrant storage. Else, this is a negative value.
  * `point`:[in,out] User-defined representation of a point. This parameter distinguishes two uses of the callback. For each quadrant, the callback is first called with a NULL point, and if this callback returns true, once for each point tracked in this branch. The return value for a point determines whether it shall be tracked further down the branch or not, and has no effect on a local leaf. The call with a NULL point is intended to prepare quadrant-related search meta data that is common to all points, and/or to efficiently terminate the recursion for all points in the branch in one call.

### Returns

If false, the recursion at **quadrant** terminates. If true, it continues if **pfirst** < **plast** or if they are both equal to `p4est`->mpirank and the recursion has not reached a leaf yet.

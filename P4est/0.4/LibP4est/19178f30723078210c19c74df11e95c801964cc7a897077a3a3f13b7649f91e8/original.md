Information about one side of a corner in the forest. If a *quad* is local (*is_ghost* is false), then its *quadid* indexes the tree's quadrant array; otherwise, it indexes the ghosts array. If a quadrant should be present, but it is not included in the ghost layer, then quad = NULL, is_ghost is true, and quadid = -1.

the *faces* field provides some additional information about the local topology: if side[i]->faces[j] == side[k]->faces[l], this indicates that there is a common face between these two sides of the corner.

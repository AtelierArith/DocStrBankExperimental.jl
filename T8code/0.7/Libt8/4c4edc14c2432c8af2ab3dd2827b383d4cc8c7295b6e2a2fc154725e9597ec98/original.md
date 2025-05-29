Callback function prototype to decide for refining and coarsening. If *is_family* equals 1, the first *num_elements* in *elements* form a family and we decide whether this family should be coarsened or only the first element should be refined. Otherwise *is_family* must equal zero and we consider the first entry of the element array for refinement.  Entries of the element array beyond the first *num_elements* are undefined.

# Arguments

  * `forest`:[in] the forest to which the new elements belong
  * `forest_from`:[in] the forest that is adapted.
  * `which_tree`:[in] the local tree containing *elements*
  * `lelement_id`:[in] the local element id in *forest_old* in the tree of the current element
  * `ts`:[in] the eclass scheme of the tree
  * `is_family`:[in] if 1, the first *num_elements* entries in *elements* form a family. If 0, they do not.
  * `num_elements`:[in] the number of entries in *elements* that are defined
  * `elements`:[in] Pointers to a family or, if *is_family* is zero, pointer to one element.

# Returns

1 if the first entry in *elements* should be refined, -1 if the family *elements* shall be coarsened, -2 if the first entry in *elements* should be removed, 0 else.

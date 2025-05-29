Callback function prototype to replace one set of elements with another.

This is used by the replace routine which can be called after adapt, when the elements of an existing, valid forest are changed. The callback allows the user to make changes to the elements of the new forest that are either refined, coarsened or the same as elements in the old forest.

If an element is being refined, *refine* and *num_outgoing* will be 1 and  *num_incoming* will be the number of children. If a family is being coarsened, *refine* will be -1, *num_outgoing* will be  the number of family members and *num_incoming* will be 1.  If an element is being removed, *refine* and *num_outgoing* will be 1 and  *num_incoming* will be 0.  Else *refine* will be 0 and *num_outgoing* and *num_incoming* will both be 1.

# Arguments

  * `forest_old`:[in] The forest that is adapted
  * `forest_new`:[in] The forest that is newly constructed from *forest_old*
  * `which_tree`:[in] The local tree containing *first_outgoing* and *first_incoming*
  * `ts`:[in] The eclass scheme of the tree
  * `refine`:[in] -1 if family in *forest_old* got coarsened, 0 if element has not been touched, 1 if element got refined and -2 if element got removed. See return of [`t8_forest_adapt_t`](@ref).
  * `num_outgoing`:[in] The number of outgoing elements.
  * `first_outgoing`:[in] The tree local index of the first outgoing element. 0 <= first_outgoing < which_tree->num_elements
  * `num_incoming`:[in] The number of incoming elements.
  * `first_incoming`:[in] The tree local index of the first incoming element. 0 <= first_incom < new_which_tree->num_elements

# See also

[`t8_forest_iterate_replace`](@ref)

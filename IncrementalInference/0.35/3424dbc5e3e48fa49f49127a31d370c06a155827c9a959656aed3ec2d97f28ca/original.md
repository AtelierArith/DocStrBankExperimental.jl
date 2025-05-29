```julia
areSiblingsRemaingNeedDownOnly(tree, cliq)

```

Return true there is no other sibling that will make progress.

Notes

  * Relies on sibling priority order with only one "currently best" option that will force progress in global upward inference.
  * Return false if one of the siblings is still busy

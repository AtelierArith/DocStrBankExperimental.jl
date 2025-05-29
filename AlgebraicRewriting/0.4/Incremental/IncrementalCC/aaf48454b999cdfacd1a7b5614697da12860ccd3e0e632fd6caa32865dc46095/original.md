Add to `matches` based on an addition #i specified via a pushout (rmap, update)

```
             For all overlaps:  apex ↪ L
                                ↓      ⇣ (find all of these!)
```

Hom(L, X*old) => Hom(L, X)         Rᵢ ⟶  X                                     rmap ⌞ ↑ update                                           X*old

However, we only want maps L → X where elements not in the image of L are all  sent to X elements which outside of the image of rmap.

This is to avoid double-counting with a slightly bigger overlap which has  already been calculated between L and Rᵢ.

Note, adding things can also invalidate old matches if there are negative application or dangling conditions.

Returns the 'keys' of the deleted matches and added matches.

```
whitebalance(c, src_white, ref_white)
```

Whitebalance a color.

Input a source (adopted) and destination (reference) white. For example, if you want a photo taken under fluorescent lighting to appear correct in regular sunlight, you might do something like `whitebalance(c, WP_F2, WP_D65)`.

# Arguments

  * `c`: An observed color.
  * `src_white`: Adopted or source white corresponding to `c`
  * `ref_white`: Reference or destination white.

Returns a whitebalanced color.

```
setblendextend(blend::Blend, mode)
```

Specify how color blend patterns are repeated/extended. Supply the blend and one of the following strings:

  * "repeat":  the pattern is repeated
  * "reflect": the pattern is reflected (repeated in reverse)
  * "pad": outside the pattern, use the closest color
  * "none": outside of the pattern, use transparent pixels

```
ininterior(p::VRepElement, h::HRepElement)
```

Returns whether `p` is in the interior of `h`. If `h` is an hyperplane, it always returns `false`. If `h` is an halfspace $\langle a, x \rangle \leq \beta$, it returns whether `p` is in the open halfspace $\langle a, x \rangle < \beta$

```
ininterior(p::VRepElement, h::HRep)
```

Returns whether `p` is in the interior of `h`, e.g. in the interior of all the hyperplanes and halfspaces supporting `h`.

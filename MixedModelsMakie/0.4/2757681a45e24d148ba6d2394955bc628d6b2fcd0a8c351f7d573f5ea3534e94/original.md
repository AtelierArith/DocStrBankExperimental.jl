```
profiledensity!(f::Indexable, pr::MixedModelProfile;
                ptyp::Char='σ',
                zbd=3,
                share_y_scale=true).
```

Add axes with density plots of the profile ζ for parameters starting with `ptyp` from `pr` to `f`.

Valid `ptyp` values are 'β', 'σ', and 'θ'.

If `share_y_scale`, the each facet shares a common y-scale.

```
zetaplot!(f::Indexable, pr::MixedModelProfile;
          absv=false,
          ptyp='β',
          coverage=[.5,.8,.9,.95,.99],
          zbd=nothing)
```

Add axes with plots of the profile ζ (or its absolute value) for parameters starting with `ptyp` from `pr` to `f`.

Valid `ptyp` values are 'β', 'σ', and 'θ'.

If `absv` is `true` then intervals corresponding to coverage levels in `coverage` are added to each panel.

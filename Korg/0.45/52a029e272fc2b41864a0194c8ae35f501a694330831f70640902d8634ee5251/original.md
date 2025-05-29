```
get_GES_linelist()
```

The Gaia-ESO survey linelist from [Heiter et al. 2021](https://ui.adsabs.harvard.edu/abs/2021A&A...645A.106H/abstract).  This linelist contains > 15 million lines, which means that it can take a while to synthesize spectra.  If you don't need molecular lines, you can set `include_molecules=false` to speed things up.

# Keyword Arguments

  * `include_molecules` (default: `true`): whether to include molecular lines.

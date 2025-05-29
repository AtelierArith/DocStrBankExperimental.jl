```julia
screen_outliers(smpl::ChronAgeData; agemin=0.0, agemax=Inf, maxgap=100, make_plots=true, discordancemin=0, discordancemax=100)
```

Screen outliers from the `ChronAgeData` struct `smpl` (making new data files in a `screened` subdirectory within `smpl.Path`) rejecting samples that either

a) Are older than `agemax` or younger than `agemin`

b) Are on the old side of a gap of more than `maxgap/N` sigma (e.g., xenocrysts)

If `make_plots` is `true`, plots showing screening results will be made in `smpl.Path/screened`.

If the underlying data is in the form of U-Pb ratios, the `discordancemin` and `discordancemax` keyword arguments may also be used for additional screening.

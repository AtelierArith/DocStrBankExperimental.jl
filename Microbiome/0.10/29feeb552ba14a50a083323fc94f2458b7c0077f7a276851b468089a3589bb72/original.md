```
set!(cp::CommunityProfile, md; namecol=:sample)
```

Add metadata (in the form of a `Tables.jl` table) a `CommunityProfile`. One column (`namecol`) should contain sample names that exist in `commp`, and other columns should contain metadata that will be added to the metadata of each sample.

```
insert!(cp::CommunityProfile, md; namecol=:sample)
```

Add metadata (in the form of a `Tables.jl` table) a `CommunityProfile`. One column (`namecol`) should contain sample names that exist in `commp`, and other columns should contain metadata that will be added to the metadata of each sample.

Before starting, this will check that every value in every row is `insert!`able, and will throw an error if not. This requires iterating over the metadata table twice, which may be slow. If performance matters, you can use `set!` instead,  though this will overwrite existing data.

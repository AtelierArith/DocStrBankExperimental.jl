```
@recompile_invalidations begin
    using PkgA
    ⋮
end
```

Recompile any invalidations that occur within the given expression. This is generally intended to be used by users in creating "Startup" packages to ensure that the code compiled by package authors is not invalidated.

```
struct Patch
    version::VersionNumber
    actions::Vector{<: AbstractPatchAction}
end
```

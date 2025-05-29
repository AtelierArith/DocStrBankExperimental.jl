```
merge(pe1::PatchEnv, pe2::PatchEnv) -> PatchEnv
```

Merge the two `PatchEnv` instances.

This is done in such a way that the following always holds:

```
patches_1 = Patch[...]
patches_2 = Patch[...]
patches = vcat(patches_1, patches_2)

pe1 = PatchEnv(patches_1)
pe2 = PatchEnv(patches_2)
pe = PatchEnv(patches)

@assert pe == merge(pe1, pe2)
```

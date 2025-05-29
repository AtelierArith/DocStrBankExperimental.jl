```
merge(pe1::PatchEnv, pe2::PatchEnv) -> PatchEnv
```

2つの`PatchEnv`インスタンスをマージします。

これは、以下が常に成り立つように行われます：

```
patches_1 = Patch[...]
patches_2 = Patch[...]
patches = vcat(patches_1, patches_2)

pe1 = PatchEnv(patches_1)
pe2 = PatchEnv(patches_2)
pe = PatchEnv(patches)

@assert pe == merge(pe1, pe2)
```

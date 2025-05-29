```
buildFamilyArray(parentVid_vid)
```

Create a vector `vid_child_Vid`, indexed by the variant id's `vid`, that has as elements the children of each variant stored as a vector of id's. For example, `vid_child_Vid[5]` is a vector `vid_child` whose elements are the `vid`'s of the children of the variant with `vid=5`.

`parentVid_vid`:    Vector indexed by the variant id's `vid`, where each element refers to that variant's parent `vid`. For example `parentVid_vid[5]` is the `vid` of the parent of the variant with `vid=5`.

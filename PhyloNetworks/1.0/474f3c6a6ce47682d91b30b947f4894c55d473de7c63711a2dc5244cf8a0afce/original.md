```
getchild(edge)
getchild(node)
getchildren(node)
```

Get child(ren) **node(s)**.

  * `getchild`: single child node of `edge`, or of `node` after checking that `node` has a single child.
  * `getchildren`: vector of all children *nodes* of `node`.

```
getchildedge(node)
```

Single child **edge** of `node`. Checks that it's a single child.

*Warning*: these functions rely on correct edge direction, via their `ischild1` field.

See also: [`getparent`](@ref), [`getpartneredge`](@ref), [`isparentof`](@ref), [`hassinglechild`](@ref).

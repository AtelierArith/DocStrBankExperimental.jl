```
getparent(edge)
getparent(node)
getparentminor(node)
getparents(node)
```

Get parental **node(s)**.

  * `getparent`: **major** (or only) parent node of `edge` or `node`
  * `getparentminor`: minor parent node of `node`
  * `getparents`: vector of all parent nodes of `node`.

```
getparentedge(node)
getparentedgeminor(node)
```

Get one parental **edge** of a `node`.

  * `getparentedge`: major parent edge. For a tree node, it's its only parent edge.
  * `getparentedgeminor`: minor parent edge, if `node` is hybrid (with an error if `node` has no minor parent).

If `node` has multiple major (resp. minor) parent edges, the first one would be returned without any warning or error.

*Warning*: these functions use the field `ischild1` of edges.

See also: [`getchild`](@ref), [`getpartneredge`](@ref).

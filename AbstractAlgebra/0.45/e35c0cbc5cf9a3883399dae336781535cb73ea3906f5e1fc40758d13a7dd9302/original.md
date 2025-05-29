```
has_gens(G::Group)
```

Test whether group $G$ has a generating set.

Many algorithms for groups make use of a (finite) generating set. But some groups don't have one (e.g. because none has been computed yet, or the group is not finitely generated). This test functions allows writing algorithms that deal with this case gracefully.

Note that the result of this function when applied to a specific group instance can change over time, as side effect of a generating set becoming available for the group.

The default implementation returns `true`.

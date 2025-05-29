`refines(P,Q)` determines if `P` is a refinement of `Q`. That is, is every part of `P` a subset of a part of `Q`? The two partitions must have the same ground set of else an error is thrown.

`refines(P,Q)` can be invoked as `P<=Q`. The variants `P<Q`, `P>=Q`, and `P>Q` operate as expected. Note that partitions are only partially ordered by refinement and one can easily construct partitions `P` and `Q` for which both `P<=Q` and `Q<=P` are false.

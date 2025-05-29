Rewrite `@nonamespace a.b.c` to `getvar(getvar(a, :b; namespace = false), :c; namespace = false)`.

This is the default behavior of `getvar`. This should be used when inheriting states from a model.

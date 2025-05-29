Rewrite `@namespace a.b.c` to `getvar(getvar(a, :b; namespace = true), :c; namespace = true)`.

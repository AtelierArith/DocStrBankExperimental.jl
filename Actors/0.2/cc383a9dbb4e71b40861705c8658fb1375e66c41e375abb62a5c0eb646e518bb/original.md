```
@msg [Msg] A B C
```

Define empty structs as message types. `Msg` is an existing abstract datatype.

To call `@msg Msg A B C` is equivalent to

```
struct A <: Msg end
struct B <: Msg end
struct C <: Msg end
```

To call `@msg D E F` is equivalent to

```
struct D end
struct E end
struct F end
```

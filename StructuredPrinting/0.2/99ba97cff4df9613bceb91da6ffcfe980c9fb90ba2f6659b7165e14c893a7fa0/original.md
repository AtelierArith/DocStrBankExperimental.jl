```
Options(;
    print_obj = Returns(true),
    highlight = Returns(false),
    recurse = x -> !any(y -> x isa y, (UnionAll, DataType)),
    custom = x -> "",
    print_type::Bool = false,
    recursion_depth::Int = 1000,
    max_type_depth::Int = 3
)
```

Printing options for `@structured_print`:

  * `print_obj` callable that returns a `Bool` indicating whether the object (& maybe type) should be printed.
  * `highlight` callable that returns a `Bool` indicating whether the object (& maybe type) should be highlighted.
  * `recurse` callable that returns a `Bool` indicating whether printing should recurse further into this object. Default is set to `x -> !any(y -> x isa y, (UnionAll, DataType))` as they are defined recursively.
  * `custom` callable that returns an empty string, which appends the printed string.
  * `print_type`: callable that returns a `Bool` indicating whether the object's type should be printed.
  * `recursion_depth`: Int indicating depth to stop recursing.
  * `max_type_depth`: Int used for depth-limited type printing.

## Example

```julia
struct Leaf{T} end

struct Branch{A,B,C}
    leafA::A
    leafB::B
    leafC::C
end

struct Tree{A,B,C}
    branchA::A
    branchB::B
    branchC::C
end

t = Tree(
    Branch(Leaf{(:A1, :L1)}(), Leaf{(:B1, :L2)}(), Leaf{(:C1, :L3)}()),
    Branch(Leaf{(:A2, :L1)}(), Leaf{(:B2, :L2)}(), Leaf{(:C2, :L3)}()),
    Branch(Leaf{(:A3, :L1)}(), Leaf{(:B3, :L2)}(), Leaf{(:C3, :L3)}()),
)

using StructuredPrinting
# Print struct alone
@structured_print t

# Print struct with type highlighted
@structured_print t Options(;print_obj= x -> x isa typeof(t.branchB))

# Print struct with Tuple of types highlighted
@structured_print t Options(;print_obj= x -> any(y-> x isa y, (typeof(t.branchB), typeof(t.branchA))))
```

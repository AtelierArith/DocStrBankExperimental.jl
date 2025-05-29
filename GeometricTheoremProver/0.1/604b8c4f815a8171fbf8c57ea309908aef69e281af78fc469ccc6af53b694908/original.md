```
@th(block)
```

macro to construct the thesis of the theorem.

### Input

block – An expression containing the thesis of the theorem, can be a single statement          or a sequence of statements between `begin...end`.

### Output

An object of type `Thesis`.

### Examples

```jldoctest
julia> @th Segment(A, O) ≅ Segment(O, C)
THESIS:
------------
AO ≅ OC
```

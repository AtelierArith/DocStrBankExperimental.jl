```
@hp(block)
```

macro to construct the hypothesis of the theorem.

### Input

block – An expression containing the hypothesis of the theorem, can be a single statement          or a sequence of statements between `begin...end`.

### Output

An object of type `Hypothesis`.

### Examples

```jldoctest
julia> @hp O := Circle(A, B, C)
POINTS:
------------
A : free
B : free
C : free
O : dependent by (1)

HYPOTHESIS:
------------
(1) OA ≅ OB ≅ OC
```

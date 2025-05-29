```
prove(hp::Hypothesis, th::Thesis[, method=RittWuMethod])
```

Proves a thereom with given hypothesis `hp` and thesis `th`.

### Input

  * `hp::Hypothesis`                  – hypothesis of the theorem
  * `th::Thesis`                      – thesis of the theorem
  * `method<:AbstractGeometricProver` – method to prove the theorem, default `RittWuMethod`.

### Output

A proof of the the theorem. The type of the output depends on the chosen method

### Algorithms

Currently the following provers are supported

  * RittWuMethod

### Examples

```jldoctest
julia> hp = @hp D := Parallelogram(A, B, C, D)
POINTS:
------------
A : free
B : free
C : free
D : dependent by (1)

HYPOTHESIS:
------------
(1) ABCD parallelogram


julia> th = @th Segment(A, B) ≅ Segment(C, D)
THESIS:
------------
AB ≅ CD


julia> prove(hp, th)
Assigned coordinates:
---------------------
A = (0, 0)
B = (u₁, 0)
C = (u₂, u₃)
D = (x₁, x₂)

Goal 1: success

Nondegeneracy conditions:
-------------------------
```

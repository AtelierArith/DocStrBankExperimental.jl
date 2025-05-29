```
prove(hp::Hypothesis, th::Thesis[, method=RittWuMethod])
```

与えられた仮説 `hp` と命題 `th` で定理を証明します。

### 入力

  * `hp::Hypothesis`                  – 定理の仮説
  * `th::Thesis`                      – 定理の命題
  * `method<:AbstractGeometricProver` – 定理を証明するための方法、デフォルトは `RittWuMethod`。

### 出力

定理の証明。出力の型は選択した方法によって異なります。

### アルゴリズム

現在、以下の証明器がサポートされています。

  * RittWuMethod

### 例

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

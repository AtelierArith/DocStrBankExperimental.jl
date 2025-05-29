`Ratios` provides `SimpleRatio`, a faster variant of `Rational`. Speed comes at the cost of greater vulnerability to overflow.

API summary:

  * `r = SimpleRatio(num, den)` is equivalent to `num // den`
  * `common_denominator` standardizes a collection of `SimpleRatio`s to have the same denominator, making some arithmetic operations among them less likely to overflow.

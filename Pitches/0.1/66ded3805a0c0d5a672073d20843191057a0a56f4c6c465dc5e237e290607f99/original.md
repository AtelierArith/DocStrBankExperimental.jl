abstract type Interval end 

Any interval type should be a subtype of `Interval`. Intervals should implement the following operations as far as possible:

  * `ic`
  * `octave(T)`
  * `isstep`
  * `chromsemi(T)`
  * `intervalclasstype(T)`
  * `Base.+`
  * `Base.-` (negation and substraction)
  * `Base.*` (with integers, both sides)
  * `Base.zero(T)`
  * `Base.sign`

Where `(T)` marks operations on the type itself.

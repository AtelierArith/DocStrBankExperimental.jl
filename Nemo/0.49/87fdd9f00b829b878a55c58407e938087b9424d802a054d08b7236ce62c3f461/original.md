```
divides(a::AbsSimpleNumFieldElem, b::AbsSimpleNumFieldElem)
```

Returns a pair consisting of a flag which is set to `true` if $b$ divides $a$ and `false` otherwise, and a number field element $h$ such that $a = bh$ if such exists. If not, the value of $h$ is undetermined.

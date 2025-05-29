`SimpleQuaternion` creates a quaternion number. The basic constructor  is `SimpleQuaternion(a,b,c,d)` which is equivalent to  `a + b*im + c*jm + d*km`.

`SimpleQuaternion(x::Real)` yields `x + 0*im + 0*jm + 0*km`.

If `z` is the `Complex` number `a+b*im` then `SimpleQuaternion(z)` yields `a + b*im + 0*jm + 0*km`.

```
eint!(rop, op, rnd)
```

Set `rop` to the exponential integral of `op`, rounded in the direction `rnd`. This is the sum of Euler’s constant, of the logarithm of the absolute value of `op`, and of the sum for k from 1 to infinity of op^k/(k·k!). For positive `op`, it corresponds to the Ei function at `op` (see formula 5.1.10 from the Handbook of Mathematical Functions from Abramowitz and Stegun), and for negative `op`, to the opposite of the E1 function (sometimes called eint1) at `−op` (formula 5.1.1 from the same reference).

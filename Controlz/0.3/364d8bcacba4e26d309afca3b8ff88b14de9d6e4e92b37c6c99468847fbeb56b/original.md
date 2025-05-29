a closed-loop transfer function that relates an output `Y` and an input `U` in a feedback loop.

the resulting closed-loop transfer function is:

```
 Y      top
--- = --------
 U    1 + g_ol
```

# example

```jldoctest
g_ol = 4 / (s + 1) * 2 / (s + 2)
top = 5 / (s + 4)
g = ClosedLoopTransferFunction(top, g_ol)
# output
closed-loop transfer function.
      top
    -------
    1 + g_ol

  top =
    5.0
-----------
1.0*s + 4.0

  g_ol =
         8.0
---------------------
1.0*s^2 + 3.0*s + 2.0
```

# attributes

  * `top::TransferFunction`: numerator
  * `g_ol::TransferFunction`: open-loop transfer function

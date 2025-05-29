```
a_direct(k::Int, l::Int, ml::Int, l′::Int, ml′::Int)
```

Coulomb angular integral - direct part:

$$
a^{k}(lm_{l};l^{\prime}m_{l^{\prime}})=(-)^{m_{l}+m_{l^{\prime}}}
(2l+1)(2l^{\prime}+1)\left(\begin{array}{ccc}
l & k & l\\
0 & 0 & 0
\end{array}\right)\left(\begin{array}{ccc}
l & k & l\\
-m_{l} & 0 & m_{l}
\end{array}\right)\left(\begin{array}{ccc}
l^{\prime} & k & l^{\prime}\\
0 & 0 & 0
\end{array}\right)\left(\begin{array}{ccc}
l^{\prime} & k & l^{\prime}\\
-m_{l^{\prime}} & 0 & m_{l^{\prime}}
\end{array}\right)
$$

#### Example:

```
a_direct(2,1,1,2,2)
    2//35

a_direct(6,3,2,3,-1)
    -250//20449
```

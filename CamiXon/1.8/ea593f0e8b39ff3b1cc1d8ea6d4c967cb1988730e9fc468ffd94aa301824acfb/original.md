```
b_exchange(k::Int, l::Int, ml::Int, l′::Int, ml′::Int)
```

Coulomb angular integral - exchange part:

$$
b^{k}(lm_{l};l^{\prime}m_{l^{\prime}})=(2l+1)(2l^{\prime}+1)
\left(\begin{array}{ccc}
l & k & l^{\prime}\\
0 & 0 & 0
\end{array}\right)^{2}\left(\begin{array}{ccc}
l & k & l^{\prime}\\
-m_{l} & (m_{l}-m_{l^{\prime}}) & m_{l^{\prime}}
\end{array}\right)^{2}
$$

#### Example:

```
b_exchange(1,1,1,2,2)
    2//5

b_exchange(6,3,2,3,-1)
    1050//20449
```

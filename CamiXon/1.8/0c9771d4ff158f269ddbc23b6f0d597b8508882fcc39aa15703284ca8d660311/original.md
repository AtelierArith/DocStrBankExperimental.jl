```
A_direct(k::Int, l::Int)
```

Shell-averaged Coulomb angular integral - direct part:

$$
A^{k}(l)=\frac{1}{w_{l}}\sum_{m_{l}=-l}^{l}2a^{k}(lm_{l};l^{\prime}m_{l^{\prime}})=\frac{2l+1}{4l+1}\left(\begin{array}{ccc}
l & k & l\\
0 & 0 & 0
\end{array}\right)^{2}\!\!=\delta_{k,0},
$$

where  $w_{l}=2(2l+1)$ is the number of electrons in the closed shell $(nl)^{w_l}$. Note that the shell average $A^{k}(l)$ is *independent of* $l$.

#### Example:

```
julia> l=2; wl=2(2l+1);

julia> [A_direct(k,l) for k=0:2l] == [1,0,0,0,0]
true

julia> [sum([2a_direct(k, l, ml, l, 0) for ml=-l:l])//wl for k=0:4] == [1,0,0,0,0]
true
```

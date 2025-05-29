```
sincmath(x::T) where{T<:Number}
```

Julia 自带 [`sinc`] 関数計算的是归一化辛格函数:

$$
sinc(x)     =   sin(πx)/(πx)
$$

此处借用 `sinc`，定义数学领域的非归一化 sinc 函数，即计算:

$$
sin(x)/x
$$

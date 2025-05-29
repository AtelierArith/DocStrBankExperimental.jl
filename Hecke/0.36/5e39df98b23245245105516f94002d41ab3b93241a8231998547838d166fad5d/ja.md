```
scale_row!(a::SRow, b::NCRingElem) -> SRow
```

$$
b \times a
$$

の（左）積を返し、$a$ の値をこの積に再代入します。行に対しては、標準の乗算は左から行われます。

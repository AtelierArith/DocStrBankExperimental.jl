```
w3j, jmin, jmax = Wigner3j!(w3j::AbstractVector{Cdouble}, j2::Integer, j3::Integer,
                            m1::Integer, m2::Integer, m3::Integer,
                            exitstatus::Union{Nothing,Ref{<:Integer}} = nothing)
```

Wigner 3j記号を計算します

$$
\left(\begin{array}{ccc}
j & j_{2} & j_{3}\\
m_{1} & m_{2} & m_{3}
\end{array}\right)
$$

`max(abs(m1), abs(j2 - j3)) <= j <= j2 + j3`を満たすすべての整数値の`j`について。`jmin`と`jmax`の値はそれぞれ`max(abs(m1), abs(j2 - j3))`と`j2 + j3`に設定されます。ベクトル`w3j`は計算された3j記号で埋められます。最初のインデックスは`j = jmin`に対応し、最初の`jnum = jmax - jmin + 1`インデックスが populated されます。

!!! note
    `w3j`は少なくともj2+j3+1要素を含むのに十分な長さでなければなりません。`w3j[jnum:j2+j3+1]`の既存の値はゼロで上書きされる可能性があります。


参照: [`Wigner3j`](@ref)

SHTOOLSページ: [`Wigner3j`](https://shtools.oca.eu/shtools/public/wigner3j.html)

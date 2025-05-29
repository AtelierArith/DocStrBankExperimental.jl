```
w3j, jmin, jmax = Wigner3j(j2::Integer, j3::Integer,
                            m1::Integer, m2::Integer, m3::Integer,
                            exitstatus::Union{Nothing,Ref{<:Integer}} = nothing)
```

Compute the Wigner 3j symbol

$$
\left(\begin{array}{ccc}
j & j_{2} & j_{3}\\
m_{1} & m_{2} & m_{3}
\end{array}\right)
$$

for all integral values of `j` that satisfy `max(abs(m1), abs(j2 - j3)) <= j <= j2 + j3`. The values of `jmin` and `jmax` are set to `max(abs(m1), abs(j2 - j3))` and `j2 + j3` respectively. The vector `w3j` contains the computed 3j symbols. Its first index corresponds to `j = jmin`, and last index corresponds to `j = jmax`.

See also: [`Wigner3j!`](@ref)

SHTOOLS page: [`Wigner3j`](https://shtools.oca.eu/shtools/public/wigner3j.html)

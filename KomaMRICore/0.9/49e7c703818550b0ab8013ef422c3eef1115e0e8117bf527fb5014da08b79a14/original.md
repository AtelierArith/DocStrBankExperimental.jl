```
spinor = Spinor(α, β)
```

Spinor(α, β) with Cayley-Klein parameters α and β. Based on "Introduction to the Shinnar-Le Roux algorithm", Patrick Le Roux (1995). A spinor is a way to represent 3D rotations, the underlying representation is a 2 X 2 complex unitary matrix ($\alpha,\beta\in\mathbb{C}$):

$$
R=\left[\begin{array}{cc}
\alpha & -\beta^{*}\\
\beta & \alpha^{*}
\end{array}\right],
$$

with $|\alpha|^2+|\beta|^2 = 1$.

This later operates on the $2\times2$ representation of $(x,y,z)$ as follows $V^{+} = R V R^{*}$.

# Arguments

  * `α`: (`::Complex{Float64}`) Cayley-Klein parameter α
  * `β`: (`::Complex{Float64}`) Cayley-Klein parameter β

# Returns

  * `spinor`: (`::Spinor`) Spinor struct

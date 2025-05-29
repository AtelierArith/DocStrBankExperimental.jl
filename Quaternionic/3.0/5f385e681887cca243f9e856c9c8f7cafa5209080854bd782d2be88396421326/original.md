```
align(a⃗, b⃗, [w])
```

Solve [Wahba's problem](https://en.wikipedia.org/wiki/Wahba%27s_problem), finding a rotation that aligns the set of points `a⃗` to a corresponding set of points `b⃗` by minimizing the distance between the first set and the rotated second set.

Here, `a⃗` and `b⃗` must be equally sized arrays of `QuatVec`s.  If present, `w` must be an equally sized array of real numbers; if not, it is taken to be 1. We define the loss function

$$
L(ℛ) ≔ Σᵢ wᵢ ‖a⃗ᵢ - ℛ b⃗ᵢ‖²
$$

where $ℛ$ is a rotation operator, and return the quaternion corresponding to the optimal $ℛ$ that minimizes this function.

Note that it is possible that the points do not uniquely determine a rotation — as when one or both sets of points is rotationally symmetric.  In that case, the loss function $L(ℛ)$ will still be minimized and the points will still be optimally aligned by the output quaternion, but that quaternion will not be unique.

# Notes

In their book [*Fundamentals of Spacecraft Attitude Determination and Control* (2014)](https://doi.org/10.1007/978-1-4939-0802-8), Markley and Crassidis say that "Davenport’s method remains the best method for solving Wahba’s problem". This method provides the optimal quaternion as the dominant eigenvector (the one with the largest eigenvalue) of a certain matrix.  We start by defining the supplementary matrix

$$
S ≔ Σᵢ wᵢ a⃗ᵢ b⃗ᵢᵀ
$$

and vector

$$
s⃗ ≔ \begin{bmatrix}
S₂₃-S₃₂ \\
S₃₁-S₁₃ \\
S₁₂-S₂₁
\end{bmatrix}.
$$

Then the key matrix is

$$
M ≔ \begin{bmatrix}
S + Sᵀ - (\mathrm{tr}S)\, I₃ & s⃗ \\
s⃗ᵀ & \mathrm{tr}S
\end{bmatrix}
$$

It is possible for this matrix to have degenerate eigenvalues, corresponding to cases where the points do not uniquely determine the rotation, as described above.

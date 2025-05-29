```
align(A, B, [w])
```

Find a `Rotor` that aligns the set of rotors `A` to a corresponding set `B` by minimizing the distance between the first set and the rotated second set.

Here, `A` and `B` must be equally sized arrays of `AbstractQuaternion`s.  If present, `w` must be an equally sized array of real numbers; if not, it is taken to be 1.  We define the loss function

$$
L(R) ≔ Σᵢ wᵢ |Aᵢ - R Bᵢ|²
$$

where $R$ is a `Rotor`, and return the quaternion corresponding to the optimal $R$ that minimizes this function.

Note that it is possible that the input data do not uniquely determine a rotor, which will happen when sum below is zero.  When this happens, the result will contain `NaN`s, but no error will be raised.  When the sum is very close to — but not exactly — zero, the accuracy of the result will be limited.  However, the loss function will not depend strongly on the result in that case.

Be aware that this function *is* sensitive to the signs of the input quaternions.  See the [`unflip`](@ref) function for one way to avoid problems related to signs.

## Notes

We can ensure that the loss function is minimized by multiplying $R$ by an exponential, differentiating with respect to the argument of the exponential, and setting that argument to 0.  This derivative should be 0 at the minimum.  We have

$$
∂ⱼ Σᵢ wᵢ |Aᵢ - \exp[vⱼ] R Bᵢ|²  →  2 ⟨ eⱼ R Σᵢ wᵢ Bᵢ Āᵢ ⟩₀
$$

where → denotes taking $vⱼ→0$, the symbol $⟨⟩₀$ denotes taking the scalar part, and $eⱼ$ is the unit quaternionic vector in the $j$ direction.  The only way for this quantity to be zero for each choice of $j$ is if

$$
R Σᵢ wᵢ Bᵢ Āᵢ
$$

is itself a pure scalar.  This, in turn, can only happen if either (1) the sum is 0 or (2) if $R$ is proportional to the *conjugate* of the sum:

$$
R ∝ Σᵢ wᵢ Aᵢ B̄ᵢ
$$

Now, since we want $R$ to be a rotor, we simply define it to be the normalized sum.

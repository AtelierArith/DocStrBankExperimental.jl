```
s = Q(φ, nxy, nz)
```

Spinor rotation matrix. Counter-clockwise rotation of `φ` with respect to the axis of rotation n=(nx, ny, nz).

Pauly, J., Le Roux, P., Nishimura, D., & Macovski, A. (1991). Parameter relations for the Shinnar-Le Roux selective excitation pulse design algorithm (NMR imaging). IEEE Transactions on Medical Imaging, 10(1), 53-65. doi:10.1109/42.75611

$$
\varphi=-\gamma\Delta t\sqrt{\left|B_{1}\right|^{2}+\left(\boldsymbol{G}\cdot\boldsymbol{x}
\right)^{2}}=-\gamma\Delta t\left\Vert \boldsymbol{B}\right\Vert
$$

$$
\boldsymbol{n}=\boldsymbol{B}/\left\Vert \boldsymbol{B}\right\Vert
$$

# Arguments

  * `φ`: (`::Real`, `[rad]`) φ angle
  * `nxy`: (`::Real`) nxy factor
  * `nz`: (`::Real`) nz factor

# Returns

  * `s`: (`::Spinor`) spinnor struct that represents the `Q` rotation matrix

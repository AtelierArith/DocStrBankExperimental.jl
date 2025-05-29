```
rotate = Rotate(pitch, roll, yaw)
```

Rotate struct. It produces a rotation in the three axes:  x (pitch), y (roll), and z (yaw). We follow the RAS (Right-Anterior-Superior) orientation,  and the rotations are applied following the right-hand rule (counter-clockwise):

![Head Rotation Axis](../assets/head-rotation-axis.svg)

The applied rotation matrix is obtained as follows: 

$$
\begin{equation}
\begin{aligned}
R &= R_z(\alpha) R_y(\beta) R_x(\gamma) \\
  &= \begin{bmatrix}
\cos \alpha & -\sin \alpha & 0 \\
\sin \alpha & \cos \alpha & 0 \\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
\cos \beta & 0 & \sin \beta \\
0 & 1 & 0 \\
-\sin \beta & 0 & \cos \beta
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 \\
0 & \cos \gamma & -\sin \gamma \\
0 & \sin \gamma & \cos \gamma
\end{bmatrix} \\
  &= \begin{bmatrix}
\cos \alpha \cos \beta & \cos \alpha \sin \beta \sin \gamma - \sin \alpha \cos \gamma & \cos \alpha \sin \beta \cos \gamma + \sin \alpha \sin \gamma \\
\sin \alpha \cos \beta & \sin \alpha \sin \beta \sin \gamma + \cos \alpha \cos \gamma & \sin \alpha \sin \beta \cos \gamma - \cos \alpha \sin \gamma \\
-\sin \beta & \cos \beta \sin \gamma & \cos \beta \cos \gamma
\end{bmatrix}
\end{aligned}
\end{equation}
$$

# Arguments

  * `pitch`: (`::Real`, `[º]`) rotation in x
  * `roll`: (`::Real`, `[º]`) rotation in y
  * `yaw`: (`::Real`, `[º]`) rotation in z

# Returns

  * `rotate`: (`::Rotate`) Rotate struct

# Examples

```julia-repl
julia> rotate = Rotate(pitch=15.0, roll=0.0, yaw=20.0)
```

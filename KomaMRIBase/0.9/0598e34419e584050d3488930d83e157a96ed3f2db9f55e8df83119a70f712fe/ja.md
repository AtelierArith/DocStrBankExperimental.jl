```
rotate = Rotate(pitch, roll, yaw)
```

Rotate構造体。これは、3つの軸（x（ピッチ）、y（ロール）、z（ヨー））での回転を生成します。RAS（右前上）方向に従い、回転は右手の法則（反時計回り）に従って適用されます：

![Head Rotation Axis](../assets/head-rotation-axis.svg)

適用される回転行列は次のように得られます：

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

# 引数

  * `pitch`: (`::Real`, `[º]`) x軸の回転
  * `roll`: (`::Real`, `[º]`) y軸の回転
  * `yaw`: (`::Real`, `[º]`) z軸の回転

# 戻り値

  * `rotate`: (`::Rotate`) Rotate構造体

# 例

```julia-repl
julia> rotate = Rotate(pitch=15.0, roll=0.0, yaw=20.0)
```

```
rotation_tensor(ψ::Number, θ::Number, ϕ::Number)
```

三次元回転行列を返します。この行列は、三つのオイラー角 $ψ$, $θ$, $ϕ$ によって記述される回転に対応しています。

$$
R(ψ,θ,ϕ) = R_x(ψ)R_y(θ)R_z(ϕ)
$$

完全な説明については、例えば [http://eecs.qmul.ac.uk/~gslabaugh/publications/euler.pdf](http://eecs.qmul.ac.uk/~gslabaugh/publications/euler.pdf) を参照してください。

この回転テンソルのパラメータ化を使用する際に、[ジャイロロック現象](https://en.wikipedia.org/wiki/Gimbal_lock) が発生する可能性があることに注意してください。

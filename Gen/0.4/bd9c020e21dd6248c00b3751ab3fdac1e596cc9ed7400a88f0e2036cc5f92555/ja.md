```
arg_grads = accumulate_param_gradients_determ!(
    gen_fn::CustomDetermGF, state, args, retgrad, scale_factor)
```

引数に関する勾配に対して、オプションでスケーリングされたパラメータの勾配累積器を増加させ、引数に関する勾配（スケーリングされていない）を返します。

前の状態と戻り値に関する勾配 $∇_y J$（`retgrad`）が与えられたとき、引数 $x$ に関する次の勾配（`arg_grads`）を返します：

$$
∇_x J
$$

また、関数の学習可能なパラメータ $Θ$ に対して、次のように勾配累積器を増加させます：

$$
s * ∇_Θ J
$$

ここで、$s$ は `scale_factor` です。

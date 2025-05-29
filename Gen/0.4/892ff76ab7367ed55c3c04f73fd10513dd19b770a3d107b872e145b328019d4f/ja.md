```
arg_grads = accumulate_param_gradients!(trace, retgrad=nothing, scale_factor=1.)
```

トレースの対数確率の勾配によってパラメータの勾配累積器を増加させ、オプションでスケーリングし、引数に関する勾配（スケーリングなし）を返します。

以前のトレース $(x, t)$ (`trace`) と戻り値に関する勾配 $∇_y J$ (`retgrad`) が与えられた場合、引数 $x$ に関する次の勾配 (`arg_grads`) を返します：

$$
∇_x \left( \log P(t; x) + J \right)
$$

`arg_grads` の長さは、`trace` を生成した関数への引数の数（任意のオプショナルな末尾引数を含む）と等しくなります。引数が `(grad)` で注釈されていない場合、`arg_grads` の対応する値は `nothing` になります。

また、関数の学習可能なパラメータ $Θ$ の勾配累積器も次のように増加させます：

$$
∇_Θ \left( \log P(t; x) + J \right)
$$

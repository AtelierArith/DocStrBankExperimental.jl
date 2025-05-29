```
(arg_grads, choice_values, choice_grads) = choice_gradients(
    trace, selection=EmptySelection(), retgrad=nothing)
```

以前のトレース $(x, t)$ (`trace`) と戻り値に関する勾配 $∇_y J$ (`retgrad`) が与えられた場合、引数 $x$ に関する次の勾配 (`arg_grads`) を返します：

$$
∇_x \left( \log P(t; x) + J \right)
$$

`arg_grads` の長さは、`trace` を生成した関数への引数の数（任意のオプショナルな末尾引数を含む）と等しくなります。引数が `(grad)` で注釈されていない場合、`arg_grads` の対応する値は `nothing` になります。

また、連続値のランダム選択であるアドレスのセット $A$ (`selection`) が与えられた場合、これらの選択の値に関する次の勾配 (`choice_grads`) を返します：

$$
∇_A \left( \log P(t; x) + J \right)
$$

勾配は、(階層的な) アドレス `addr` における値が $∂J/∂t[\texttt{addr}]$ である選択マップとして表されます。

また、$A$ に制限された $t$ である選択マップ (`choice_values`) も返します。

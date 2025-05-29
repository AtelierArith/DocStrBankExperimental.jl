```
add_input_differentiator(sys::StateSpace, ui = 1:sys.nu; goodwin=false)
```

`sys`の出力を`u(k+1)-u(k)`の差分で拡張します。

# 引数:

  * `ui`: 微分する入力を示すインデックスまたはインデックスのベクトル。
  * `goodwin`: trueの場合、差分演算子はGoodwin δ演算子を使用します。すなわち、`(u(k+1)-u(k)) / sys.Ts`。

拡張されたシステムは次の行列を持ちます。

```
[A 0; 0 0]  [B; I]  [C 0; 0 -I]  [D; I]
```

`length(ui)`の追加状態と出力があります。

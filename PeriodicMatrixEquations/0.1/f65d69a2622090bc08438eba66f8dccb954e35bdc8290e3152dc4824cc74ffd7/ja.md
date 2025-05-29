```
 psplyapd(A, C; adj = true, rtol = ϵ^(3/4)) -> U
```

周期的離散時間リャプノフ行列方程式の解 `X = U'U` の上三角因子 `U` を計算します。

```
  A'σXA + C'C = X, if adj = true,
```

または、周期的離散時間リャプノフ行列方程式の解 `X = UU'` の

```
  AXA' + CC' =  σX, if adj = false,
```

ここで `σ` は前方シフト演算子 `σX(i) = X(i+1)` です。周期的行列 `A` は安定でなければならず、すなわちすべての特性乗数の絶対値が1未満である必要があります。

周期的行列 `A` と `C` は、3次元配列として保存されるか、行列のベクトルとして保存されます。

[1] の反復法（アルゴリズム5）とその双対バージョンが使用されます。

*参考文献:*

[1] A. Varga, "Periodic Lyapunov equations: some applications and new algorithms",      Int. J. Control, vol. 67, pp. 69-87, 1997.

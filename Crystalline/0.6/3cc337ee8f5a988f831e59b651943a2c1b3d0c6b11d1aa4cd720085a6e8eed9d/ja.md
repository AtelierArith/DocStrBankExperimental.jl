```
compose(op::SymOperation, kv::KVec[, checkabc::Bool=true])  -->  KVec
```

合成 `op` $= \{\mathbf{W}|\mathbf{w}\}$ と逆格子ベクトル `kv` $= \mathbf{k}$ を返します。

この操作は、直接格子基底で指定され、`kv` は逆格子基底で指定されていると仮定されます。両方が直交基底で指定されている場合、`op` はその回転部分を介して直接作用します。しかし、異なる基底のため、次のように作用します：

$$
    \mathbf{k}' = (\mathbf{W}^{\text{T}})^{-1}\mathbf{k}.
$$

$$
\{\mathbf{W}|\mathbf{w}\}
$$

の暗黙の実空間基底と $\mathbf{k}$ の逆空間基底の結果として、$\mathbf{W}$ の転置 *および* 逆行列に注意してください。また、回転された（平行移動なし、$\mathbf{w} = \mathbf{0}$）ベクトル $\mathbf{k}'$ と $\mathbf{r}'$ に対して、$\mathbf{k} \cdot \mathbf{r} = \mathbf{k}' \cdot \mathbf{r}'$ である必要があります。

また、$\{\mathbf{W}|\mathbf{w}\}$ と $\mathbf{k}$ の合成は $\mathbf{w}$ に依存しないことに注意してください。すなわち、平行移動は逆空間では作用しません。

## 拡張ヘルプ

`checkabc = false` の場合、`KVec` の自由部分は変換されません（`kabc` がゼロであり、いくつかの変換が要求される状況でパフォーマンスを向上させることができます）。

```
CertainValue
```

不確実性のない値（すなわちスカラーで表される）用のシンプルなラッパータイプです。

## 例

不確実性のない値を構築する次の2つの方法は同等です。

```julia
u1, u2 = CertainValue(2.2), CertainValue(6)
w1, w2 = UncertainValue(2.2), UncertainValue(6)
```

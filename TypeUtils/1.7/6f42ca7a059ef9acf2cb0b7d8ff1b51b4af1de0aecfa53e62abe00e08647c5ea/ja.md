```
floating_point_type(args...) -> T <: AbstractFloat
```

は、引数 `args...` によって使用される昇格された数値型を表す適切な浮動小数点型を返します。引数の単位は無視され、返される型は常に単位なしです。

数値計算における典型的な使用法は次のとおりです：

```
T = floating_point_type(x, y, ...)
xp = convert_real_type(T, x)
yp = convert_real_type(T, y)
...
```

これは、数値 `x`、`y` などを適切な共通の浮動小数点型に変換し、単位がある場合はそれを保持します。

また、[`real_type`](@ref) および [`convert_real_type`](@ref) も参照してください。

---

```
floating_point_type() -> AbstractFloat
```

は、引数なしで呼び出されたときに `floating_point_type` によって返される可能性のある型のスーパタイプを返します。

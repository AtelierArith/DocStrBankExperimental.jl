```
dirac(X::AbstractVector{<:AbstractMoment}, s::AbstractSubstitution...)
```

`X`のモーメントを`s`を使用して評価することによって、ディラック測度を作成します。

## 例

`dirac([x*y, x*y^2], x=>3, y=>2)`を呼び出すと、値が`6`のモーメント`x*y`と値が`12`のモーメント`x*y^2`を持つ測度が得られます。

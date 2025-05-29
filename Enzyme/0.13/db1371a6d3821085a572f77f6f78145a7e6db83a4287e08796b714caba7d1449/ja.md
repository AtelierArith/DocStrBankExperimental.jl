```
autodiff(::ReverseMode, f, Activity, args::Annotation...)
```

関数 `f` を引数 `args` で逆モードを使用して自動微分します。

制限事項：

  * `f` は `Real`（組み込み/プリミティブ型）または `nothing` を返すことができ、配列、構造体、`BigFloat` などは返せません。ベクトル値の返り値を処理するには、`nothing` を返し、その返り値を引数の1つに格納するミューテイティング `f!` を使用する必要があります。この引数は [`Duplicated`](@ref) でラップされている必要があります。

`args` は数値、配列、数値の構造体、配列の構造体などである可能性があります。Enzyme は [`Active`](@ref) でラップされた引数（プリミティブ型やその構造体のように、結果の導関数をその場で変更するのではなく返す必要がある引数）または [`Duplicated`](@ref) でラップされた引数（配列、`Ref` などのミュータブル引数）に関してのみ微分を行います。

`Activity` は返り値のアクティビティで、`Const` または `Active` である可能性があります。

例：

```jldoctest
a = 4.2
b = [2.2, 3.3]; ∂f_∂b = zero(b)
c = 55; d = 9

f(a, b, c, d) = a * √(b[1]^2 + b[2]^2) + c^2 * d^2
∂f_∂a, _, _, ∂f_∂d = autodiff(Reverse, f, Active, Active(a), Duplicated(b, ∂f_∂b), Const(c), Active(d))[1]

# 出力

(3.966106403010388, nothing, nothing, 54450.0)
```

ここで、`autodiff` はタプル $(\partial f/\partial a, \partial f/\partial d)$ を返し、$\partial f/\partial b$ は `∂f_∂b` に *加算されます*（ただし返されません）。`c` は `Const(c)` として扱われます。

計算の元の返り値を要求することもできます。

例：

```jldoctest
Enzyme.autodiff(ReverseWithPrimal, x->x*x, Active(3.0))

# 出力

((6.0,), 9.0)
```

!!! 注     Enzyme の整数値に関する勾配はゼロです。[`Active`](@ref) は通常の整数を浮動小数点値に自動的に変換しますが、タプルや構造体内の整数値については変換できません。 ```

```
autodiff(::ForwardMode, f, Activity, args::Annotation...)
```

関数 `f` を引数 `args` で前方モードを使用して自動微分します。

`args` は数値、配列、数値の構造体、配列の構造体などである可能性があります。Enzyme は [`Duplicated`](@ref) または類似の引数でラップされた引数に対してのみ微分を行います。 [`autodiff`](@ref) の逆モードとは異なり、すべての不変オブジェクトの導関数結果が返されるため、ここでは [`Active`](@ref) 引数は許可されておらず、代わりに [`Duplicated`](@ref) または [`DuplicatedNoNeed`](@ref) のような変種を使用する必要があります。

`Activity` は戻り値のアクティビティであり、次のようになります：

  * `Const` は戻り値が微分されない場合
  * `Duplicated` は戻り値が微分される場合
  * `BatchDuplicated` は `Duplicated` のように、複数の導関数を一度に計算します。すべての引数のバッチサイズは同じでなければなりません。

元の戻り値と導関数の両方を返す例：

```jldoctest
f(x) = x*x
res, ∂f_∂x = autodiff(ForwardWithPrimal, f, Duplicated, Duplicated(3.14, 1.0))

# output

(6.28, 9.8596)
```

導関数のみを返す例：

```jldoctest
f(x) = x*x
∂f_∂x = autodiff(Forward, f, Duplicated, Duplicated(3.14, 1.0))

# output

(6.28,)
```

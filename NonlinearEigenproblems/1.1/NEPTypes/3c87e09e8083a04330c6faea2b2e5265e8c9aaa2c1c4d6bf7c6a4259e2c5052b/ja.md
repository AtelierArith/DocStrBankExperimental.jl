```
abstract type Errmeasure; end
```

`Errmeasure`の具体的なサブタイプは、固有対の誤差を測定する特定の方法を表します。NEPソルバーは、そのようなオブジェクトを入力として受け取ります。NEPソルバーのユーザーとして、次のようにタイプを使用します。

```julia
julia> quasinewton(nep,errmeasure=ResidualErrmeasure(nep))
```

ユーザーが指定した誤差測定方法は、`Errmeasure`の新しいサブタイプを作成し、それを`errmeasure`キーワードとして使用することで提供できます。誤差を測定する方法は、`estimate_error`メソッドで指定する必要があります。

実際には、`Function`を`Errmeasure`オブジェクトの代わりに使用することができ、これはユーザー定義の誤差測定を持つ簡単な方法です。[`ErrmeasureType`](@ref)を参照してください。

関連情報: [`ErrmeasureType`](@ref), [`DefaultErrmeasure`](@ref), [`ResidualErrmeasure`](@ref), [`StandardSPMFErrmeasure`](@ref), [`estimate_error`](@ref), [`EigvalReferenceErrmeasure`](@ref).

```julia
flip(x::Bool)

flip(x::Union{R, I}) where {R<:Real, I<:Int}
```

実数または整数の符号を反転し、ブール値を否定します。

この関数は、[`_permTest!`](@ref) または [`_permMcTest!`](@ref) を呼び出すための引数 `fstat` に必要になる場合があります。自分のテストを作成する場合は、[自分のテストを作成する](@ref "Create your own test")を参照してください。 [Chatterjee相関](@ref "Example 5: univariate Chatterjee correlation")のテストを作成する方法の例を見てください。

また、独自のテスト統計量を計算するために開発するコードで新しいテストを作成する際にも役立ちます。

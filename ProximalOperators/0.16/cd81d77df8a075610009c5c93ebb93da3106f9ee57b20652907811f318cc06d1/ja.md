```
IndPSD(;scaling=false)
```

正準半定錐の指標を返します

$$
C = \{ X : X \succeq 0 \}.
$$

関数への引数は、`Symmetric`、`Hermitian`、または`AbstractMatrix`オブジェクト、または対称行列を（下三角）パックストレージに保持する`AbstractVector{Float64}`型のオブジェクトである必要があります。

`scaling = true`の場合、`prox!(y::AbstractVector{Float64}, f::IndPSD, x::AbstractVector{Float64}, args...)`内のベクトル`y`と`x`のオフダイアゴナル要素は、内積を保持するために`√2`で乗算されます。詳細はVandenberghe 2010を参照してください: http://www.seas.ucla.edu/~vandenbe/publications/coneprog.pdf 。

すなわち、`scaling=true`の場合、`X,Y`を行列とし、

`x = (X_{1,1}, √2⋅X_{2,1}, ... ,√2⋅X_{n,1}, X_{2,2}, √2⋅X_{3,2}, ..., X_{n,n})`、

`y = (Y_{1,1}, √2⋅Y_{2,1}, ... ,√2⋅Y_{n,1}, Y_{2,2}, √2⋅Y_{3,2}, ..., Y_{n,n})`

とすると、`prox!(Y, f, X)`は`prox!(y, f, x)`に相当します。

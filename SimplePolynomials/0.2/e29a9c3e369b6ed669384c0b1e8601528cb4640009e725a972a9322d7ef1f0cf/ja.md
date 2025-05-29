`make_function(p::SimplePolynomial)` または `make_function(f::SimpleRationalFunction)` は、`p` または `f` を評価する Julia の `Function` を返します。もちろん、`p(x)` または `f(x)` を使用することもできますが、返された関数はその後（例えば）`plot` に渡すことができます。

`p(x)` [または `f(x)`] はすでに非常に効率的であることに注意してください。

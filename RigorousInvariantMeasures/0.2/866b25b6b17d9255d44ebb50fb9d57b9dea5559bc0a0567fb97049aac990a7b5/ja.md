```
value_and_derivative(f, x)
```

f(x) と f'(x) を同時に評価します。関数とその導関数の間に共有される部分式があることが多いため、または自動微分パッケージによって一緒に計算されるため、これを行う単一のメソッドを定義します。したがって、f と f' のために2つの別々の関数を持ち、それらを別々に呼び出すよりも、しばしば効率的です。

一般的な実装は、導関数を計算するために `TaylorSeries` を使用します。個々の関数に対して上書きすることができます：

```
f = x -> x^2
value_and_derivative(f::typeof(f), x) = (x^2, 2x)
```

3つの別々の式で導関数を定義するには @define*with*derivatives を参照してください。

注：導関数を手動で特化する際は、常に2引数の関数（例：`value_and_derivative(f, x)`）を特化し、1引数の関数（例：`value_and_derivative(f)`）を特化しないでください。後者は前者に基づいて一般的に定義されています。

注：微妙なバグを引き起こす可能性のあるトリッキーなポイント：同じ行のコードで作成された関数は、しばしば同じ型を持ちます。たとえば、

# ```jldoctest

# julia> fs = [x -> k*x for k in 1:3];  # ここにある3つの要素は同じ型を持っています

# julia> typeof(fs[1]) == typeof(fs[3])

# true

# julia> RigorousInvariantMeasures.derivative(f::typeof(fs[1]), x) = 1;

# julia> RigorousInvariantMeasures.derivative(f::typeof(fs[2]), x) = 2;

# julia> RigorousInvariantMeasures.derivative(f::typeof(fs[3]), x) = 3;

# julia> RigorousInvariantMeasures.derivative(fs[1], 0.5)  # これは1ではなく3を返します

# 3

# ```

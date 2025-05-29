```
Precompose(f, L, μ, b)
```

関数を返します

$$
g(x) = f(Lx + b)
$$

ここで、$f$ は凸関数であり、$L$ は線形写像です：これは $LL^* = μI$ を満たさなければなりません、$μ > 0$ の場合。さらに、$f$ が分離可能であるか、パラメータ `μ` がスカラーである必要があります。そうでないと、$g$ の `prox` を計算できません。

パラメータ `L` は `mul!` メソッドを通じて $L$ を定義します。したがって、`L` は例えば `AbstractMatrix` であることができますが、必ずしもそうである必要はありません。

この場合、`prox` と `prox!` は Bauschke, Combettes の "Convex Analysis and Monotone Operator Theory in Hilbert Spaces" の Prop. 24.14 に従って計算されます。結果は同じ本の第1版の Prop. 23.32 でもあります。

```
pddl"..."
```

文字列 `"..."` を PDDL 構造体に解析します。

PDDL 形式を解析する際、変数 `x` は `$x` の構文を使用して文字列に埋め込むことができます。例えば、`pddl"(on $x $y)"` は、`x` と `y` が [`Term`](@ref) の場合、`Compound(:on, Term[x, y])` に解析されます。

Julia の式は、式を波括弧で囲むことによって埋め込むことができます。すなわち、`${...}` です。 ```

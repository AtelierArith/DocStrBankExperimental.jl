```
Pipeline{name}(f)
```

名前付きのパイプライン関数を作成します。パイプライン関数を呼び出すと、結果に `name` がマークされます。 `f` は2つの引数を取る必要があります：入力と、結果がマージされる名前付きタプル（無視しても構いません）。 `name` は `Symbol` または `Symbol` のタプルのいずれかです。

```
Pipeline{name}(f, n)
```

名前付きのパイプライン関数を作成します。 `f` は1つの引数を取り、`n` の値に応じて入力または名前付きタプルのいずれかに適用されます。 `n` は `1` または `2` のいずれかでなければなりません。これは `f(n == 1 ? source : target)` と同等です。

```
Pipeline{name}(f, syms)
```

名前付きのパイプライン関数を作成します。 `syms` は `Symbol` または `Symbol` のタプルのいずれかです。これは `f(target[syms])` または `f(target[syms]...)` に等しく、`syms` の型によって異なります。

# 例

```julia-repl
julia> p = Pipeline{:x}(1) do x
           2x
       end
Pipeline{x}(var"#19#20"()(source))

julia> p(3)
(x = 6,)

julia> p = Pipeline{:x}() do x, y
           y.a * x
       end
Pipeline{x}(var"#21#22"()(source, target))

julia> p(2, (a=3, b=5))
(a = 3, b = 5, x = 6)

julia> p = Pipeline{:x}(y->y.a^2, 2)
Pipeline{x}(var"#23#24"()(target))

julia> p(2, (a = 3, b = 5))
(a = 3, b = 5, x = 9)

julia> p = Pipeline{(:sinx, :cosx)}(sincos, 1)
Pipeline{(sinx, cosx)}(sincos(source))

julia> p(0.5)
(sinx = 0.479425538604203, cosx = 0.8775825618903728)

julia> p = Pipeline{:z}((x, y)-> 2x+y, (:x, :y))
Pipeline{z}(var"#33#34"()(target.x, target.y))

julia> p(0, (x=3, y=5))
(x = 3, y = 5, z = 11)

```

```
lambdify(ex, vars...;
         fns=Dict(), values=Dict,
         expression = Val{false},
         conv = walk_expression,
         use_julia_code=false,
         invoke_latest=true)
```

シンボリック式を受け取り、`Function`をサブタイプ化する`Julia`構造体または関数を構築するための式を返します。この構造体は式を含みます。

  * `ex::Sym` 自由なシンボルが0、1、またはそれ以上含まれるシンボリック式
  * `vars` 変数のタプル、またはそれぞれを個別にリストしたもの。デフォルトは`free_symbols(ex)`とその順序です。`vars`が空の場合、引数なしの関数が返されます。
  * `fns::Dict`, `vals::Dict`: シンボリック式`ex`を走査し、対応するASTを`Julia`の式に作成する関数をカスタマイズするための辞書です。`SymPy.fn_map`および`SymPy.val_map`を参照して、sympy関数と値のデフォルトマッピングを`Julia`のASTに変換します。

# `expression`: デフォルトは`Val{false}`で、呼び出し可能な構造体を返します。`Val{true}`を渡すと式が返されます。（これは構造体の`expr`フィールドにも含まれているため、これを変更する必要はありません。）（`invoke_latest=false`も参照してください。）

  * `conv`: シンボリック式を式に変換するためのメソッド。デフォルトはこのパッケージの一部であり、代替の未公開の`julia_code`はPythonパッケージからのものです。（`use_julia_code`も参照してください。）
  * `use_julia_code::Bool`: SymPyの式への変換を使用します。デフォルトは`false`です。
  * `invoke_latest=true`: `true`の場合、`eval`および`Base.invokelatest`を呼び出して、ワールドエイジの問題がない関数を返します。`false`の場合、関数を生成するために`eval`できる`Julia`の式が返されます。

例:

```jldoctest lambdify
julia> using SymPyPythonCall

julia> @syms x y z
(x, y, z)

julia> ex = x^2 * sin(x)
 2
x ⋅sin(x)

julia> fn = lambdify(ex);

julia> fn(pi)
0.0

julia> ex = x + 2y + 3z
x + 2⋅y + 3⋅z

julia> fn = lambdify(ex);

julia> fn(1,2,3) # order is by free_symbols
14

julia> ex(x=>1, y=>2, z=>3)
14

julia> fn = lambdify(ex, (y,x,z));

julia> fn(1,2,3)
13
```

!!! note
    デフォルトでは、`eval`および`Base.invokelatest`への呼び出しのため、生成される関数が遅くなります。以下の`g2`（追加の計算が必要であることがわかる）は、非シンボリック型の`f`を呼び出すのと同じくらい速いですが、`g1`はこの例では桁違いに遅くなります。


```julia lambdify
julia> @syms x
(x,)

julia> f(x) = exp(cot(x))
f (generic function with 1 method)

julia> g1 = lambdify(f(x));

julia> ex = lambdify(f(x), invoke_latest=false);

julia> @eval g2(x) = ($ex)(x)
g2 (generic function with 1 method)
```

パフォーマンスが高く簡単な代替手段として、`GeneralizedGenerated`の`mk_function`を使用することができます。以下のように：

```julia
julia> using GeneralizedGenerated, BenchmarkTools

julia> f(x,p) = x*tanh(exp(p*x));

julia> @syms x p; g = lambdify(f(x,p), x, p)
Callable function with variables (:x, :p)

julia> gg = mk_function(g...);

julia> @btime $g(1,2)
  48.862 ns (1 allocation: 16 bytes)
0.9999992362042291

julia> @btime $gg(1,2)
 1.391 ns (0 allocations: 0 bytes)
0.9999992362042291

julia> @btime $f(1,2)
  1.355 ns (0 allocations: 0 bytes)
0.9999992362042291

```

見たように、`GeneralizedGenerated`によって生成された関数は元の関数と同じくらいパフォーマンスが高く、**はるかに**`Base.invokelatest`への呼び出しを使用する`lambdify`によって返された関数よりも優れています。 ```

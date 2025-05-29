```
@register(model::InfiniteModel, func_expr, [gradient::Function], [hessian::Function])
```

`func_expr`に従ってユーザー定義関数を登録し、`model`と共に使用される`NLPExpr`でトレースされることなく使用できるようにします。

**引数情報** ここで`func_expr`は`myfunc(a, b)`の形であり、`myfunc`は関数名で、引数の数は象徴的に与えられます。引数のシンボルの選択は任意です。各関数引数は、指定された`Real`型の任意のものをサポートする必要があります。

ここでは、1引数関数のための勾配関数`gradient`も指定できます。この関数は1つの引数を受け取り、その導関数を返す必要があります。多引数関数の場合、勾配関数は次の形でなければなりません：

```julia
function gradient(g::AbstractVector{T}, args::T...) where {T <: Real}
    # 関数の勾配でgベクトルを埋める
end
```

1引数関数の場合、引数を受け取り2次導関数を返すヘッセ行列関数を指定することもできます。多引数関数に対してヘッセ行列を指定することもできますが、`JuMP`バックエンドは現在これをサポートしていません。

勾配および/またはヘッセ行列が指定されていない場合、バックエンドの自動微分機能（例：`JuMP`）がそれらを決定するために使用されます。`JuMP`バックエンドは、ユーザー定義の多引数関数に対してヘッセ行列を使用しないことに注意してください。

**注意事項**

  * 可能な場合、関数を登録するよりもトレースを優先します（詳細については[Function Tracing](@ref)を参照してください）。
  * ユーザー定義の関数のみを指定できます。関数がパッケージによって使用されている場合、直接使用することはできません。ただし、新しい関数`newfunc(a) = pkgfunc(a)`でラップすることは容易です。
  * 定義されたスコープ内でのみ関数を登録できます。
  * 登録された関数は、登録されたスコープ内またはその下でのみ使用できます。たとえば、別の関数内で関数を登録した場合、その関数内でのみ使用できます（外部では使用できません）。
  * 特定のモデル内で、与えられた名前と引数の数を持つ関数は1回だけ登録できます。

**例**

```julia-repl
julia> @variable(model, x)
x

julia> f(a) = a^3;

julia> f(x) # ユーザー関数がトレースされる
x^3

julia> @register(model, f(a)) # 関数を登録
f (generic function with 2 methods)

julia> f(x) # 関数はもはやトレースされず、自動微分が使用される
f(x)

julia> f2(a) = a^2; g2(a) = 2 * a; h2(a) = 2;

julia> @register(model, f2(a), g2, h2) # 明示的な勾配とヘッセ行列で登録
f2 (generic function with 2 methods)

julia> f2(x)
f2(x)

julia> f3(a, b) = a * b^2;

julia> function g3(v, a, b)
          v[1] = b^2
          v[2] = 2 * a * b
          return
       end;

julia> @register(model, f3(a, b), g3) # 多引数関数を登録
f3 (generic function with 4 methods)

julia> f3(42, x)
f3(42, x)
```

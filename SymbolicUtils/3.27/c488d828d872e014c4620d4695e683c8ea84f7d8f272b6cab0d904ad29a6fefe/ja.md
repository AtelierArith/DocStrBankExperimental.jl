```
PolyForm{T} <: Symbolic
```

[MultivariatePolynomials.jl](https://juliaalgebra.github.io/MultivariatePolynomials.jl/stable/)をSymbolicUtils式として抽象化し、その逆も行います。

SymbolicUtilsの項インターフェース（`isexpr`/`iscall`、`operation`、および`arguments`）は、PolyFormに対して遅延的に機能します：`operation`と`arguments`は、引数の1レベルをSymbolicUtils式に変換することによって作成されます。それらはさらにPolyFormを含む場合があります。これは、`simplify_fractions`を行う際に多項式をメモリに保持するために使用します。

```
PolyForm{T}(x; Fs=Union{typeof(*),typeof(+),typeof(^)}, recurse=false)
```

Symbolic式`x`を多項式に変換し、それを抽象化したPolyFormを返します。

`Fs`は、引数自体が多項式化される場合に適用されるべき関数の型です。たとえば、べき乗式の基数のみを多項式化したい場合は、`typeof(^)`をユニオンから省略します。この場合、`^`は呼び出されず、`Pow`項として保持されます。

`recurse`は、サブ式に対して再帰的に`PolyForm`を呼び出すフラグです。たとえば：

```julia
PolyForm(sin((x+y)^2))               #=> sin((x+y)^2)
PolyForm(sin((x+y)^2), recurse=true) #=> sin((x^2 + (2x)y + y^2))
```

@fastfunc functionname polynomial

数値評価のための高速関数を生成します。生成された関数の入力引数の数は、入力多項式の変数の数と一致します。

多項式は `@fastmath` を使用して変換され、これは厳密なIEEEセマンティクスに違反する可能性のある関数を呼び出します。

多項式の評価を数回だけ行う予定の場合は、標準的な方法を使用してください（詳細についてはTypedPolynomialsを参照）。大量の評価を行う場合にのみ、この方法で生成された関数とトータルで釣り合うことができます。

# 例

```
julia> using SphericalHarmonics

julia> @polyvar x y z
(x, y, z)

julia> p = 15.0*x*y^2+7.5*x*z^13
7.5xz¹³ + 15.0xy²

julia> foo = @fastfunc p

julia> foo(1.0,2.0,3.0)
1.19574825e7
```

# 非グローバルスコープ

ローカルスコープ内からの使用は、問題#4を避けるために特別な注意が必要です。したがって、`foo(1.0,2.0,3.0)` の代わりに `Base.invokelatest(foo, 1.0,2.0,3.0)` を使用する必要があります。

```
julia> using SphericalHarmonics

julia> @polyvar x y z
(x, y, z)

julia> function useInsideFunctionScope()
           p = 15.0*x*y^2+7.5*x*z^13
           foo = @fastfunc p
           Base.invokelatest(foo, 1.0,2.0,3.0)
       end
useInsideFunctionScope (generic function with 1 method)

julia> useInsideFunctionScope()
1.19574825e7
```

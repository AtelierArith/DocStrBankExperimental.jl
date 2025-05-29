```
@force_nonlinear(expr)
```

`expr`の解析を変更して、[`GenericNonlinearExpr`](@ref)を構築するようにします。これは[`GenericAffExpr`](@ref)や[`GenericQuadExpr`](@ref)の代わりです。

このマクロは`expr`を歩き、`+`、`-`、`*`、`/`、および`^`へのすべての呼び出しを、[`GenericNonlinearExpr`](@ref)を構築するものに置き換えることによって機能します。

このマクロは、結果の式が[`GenericNonlinearExpr`](@ref)を生成しない場合にエラーになります。たとえば、基本的な算術演算子を使用しない式に対して使用された場合です。

## このマクロを使用するタイミング

ほとんどの場合、このマクロを使用すべきではありません。

意図した出力タイプが[`GenericNonlinearExpr`](@ref)であり、通常のマクロ呼び出しが問題の構造を破壊する場合、またはまれに、通常のマクロ呼び出しが大量の中間変数を導入する場合（たとえば、共通の二次式に型を昇格させるため）にのみ、このマクロを使用してください。

## 例

### 使用例1: 問題の構造を保持する。

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @expression(model, (x - 0.1)^2)
x² - 0.2 x + 0.010000000000000002

julia> @expression(model, @force_nonlinear((x - 0.1)^2))
(x - 0.1) ^ 2

julia> (x - 0.1)^2
x² - 0.2 x + 0.010000000000000002

julia> @force_nonlinear((x - 0.1)^2)
(x - 0.1) ^ 2
```

### 使用例2: アロケーションを削減する

この例では、`x * 2.0 * (1 + x) * x`が非線形式を構築することがわかっています。

しかし、デフォルトの解析は最初に次のものを構築します：

  * [`GenericAffExpr`](@ref) `a = x * 2.0`,
  * 別の[`GenericAffExpr`](@ref) `b = 1 + x`
  * [`GenericQuadExpr`](@ref) `c = a * b`
  * [`GenericNonlinearExpr`](@ref) `*(c, x)`

対照的に、修正された解析は次のものを構築します：

  * [`GenericNonlinearExpr`](@ref) `a = GenericNonlinearExpr(:+, 1, x)`
  * [`GenericNonlinearExpr`](@ref) `GenericNonlinearExpr(:*, x, 2.0, a, x)`

これにより、アロケーションが大幅に減少します。

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @expression(model, x * 2.0 * (1 + x) * x)
(2 x² + 2 x) * x

julia> @expression(model, @force_nonlinear(x * 2.0 * (1 + x) * x))
x * 2.0 * (1 + x) * x

julia> @allocated @expression(model, x * 2.0 * (1 + x) * x)
3680

julia> @allocated @expression(model, @force_nonlinear(x * 2.0 * (1 + x) * x))
768
```

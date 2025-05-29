```
@hassert(S::Symbol, k::Int, assert::Expr)
@hassert S k assert

@hassert(S::Symbol, assert::Expr)
@hassert S assert
```

このマクロは、コード内のアサーションチェックを制御するために使用できます。

マクロ `@hassert` は、*アサーションスコープ* を指定するシンボル `S`、オプションの整数 `k`、およびアサーション `assert` の2つまたは3つの引数を取ります。`k` が指定されていない場合、デフォルトで $1$ に設定されます。

各アサーションスコープ `S` には、キャッシュされた *アサーションレベル* `l` が関連付けられています。`S` のアサーションレベル $l$ が `k` 以上である場合、マクロ `@hassert` はアサーション `assert` のチェックをトリガーします。`assert` が間違っている場合、`AssertionError` がスローされます。

新しいアサーションスコープを追加するには、関数 [`add_assertion_scope`](@ref) を呼び出します。

新しいインスタンスを開始すると、すべてのアサーションレベルは $0$ に設定されます。アサーションスコープのアサーションレベルを調整するには、関数 [`set_assertion_level`](@ref) を呼び出します。

アサーションスコープの現在のアサーションレベルにアクセスするには、関数 [`get_assertion_level`](@ref) を呼び出します。

# 例

このマクロの使い方を示すために、異なるアサーションレベルを持つ異なるアサーションスコープをカスタム関数で設定します。

```jldoctest
julia> AbstractAlgebra.add_assertion_scope(:MyScope)

julia> AbstractAlgebra.get_assertion_level(:MyScope)
0

julia> function hassert_test(x::Int)
       @hassert :MyScope 700 mod(x, 3) == 0
       return div(x, 3)
       end
hassert_test (generic function with 1 method)

julia> hassert_test(2)
0

julia> AbstractAlgebra.set_assertion_level(:MyScope, 701);

julia> try hassert_test(2)
       catch e e
       end
AssertionError("\$(Expr(:escape, :(mod(x, 3) == 0)))")

julia> hassert_test(3)
1

julia> AbstractAlgebra.set_assertion_level(:MyScope, 0)
0
```

事前にアサーションスコープを設定しない場合、マクロは「Not a valid symbol」というエラーメッセージを表示する `ExceptionError` を発生させます。

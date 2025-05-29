```
@v_do(S::Symbol, k::Int, act::Expr)
@v_do S k act

@v_do(S::Symbol, act::Expr)
@v_do S act
```

このマクロは、コード内のアクションを制御するために使用できます。

マクロ `@v_do` は、シンボル `S`（*冗長性スコープ*を指定）、オプションの整数 `k`、およびアクション `act` の2つまたは3つの引数を取ります。`k` が指定されていない場合、デフォルトで $1$ に設定されます。

各冗長性スコープ `S` には、*冗長性レベル* `l` が関連付けられています。`S` の冗長性レベル $l$ が `k` 以上である場合、マクロ `@v_do` はアクション `act` をトリガーします。

新しい冗長性スコープを追加するには、関数 [`add_verbosity_scope`](@ref) を呼び出します。

新しいインスタンスを開始すると、すべての冗長性レベルは $0$ に設定されます。冗長性スコープの冗長性レベルを調整するには、関数 [`set_verbosity_level`](@ref) を呼び出します。

冗長性スコープの現在の冗長性レベルにアクセスするには、関数 [`get_verbosity_level`](@ref) を呼び出します。

# 例

このマクロの使い方を示すために、異なる冗長性レベルを持つ異なる冗長性スコープをカスタム関数で設定します。

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:Test1);

julia> AbstractAlgebra.add_verbosity_scope(:Test2);

julia> AbstractAlgebra.add_verbosity_scope(:Test3);

julia> AbstractAlgebra.set_verbosity_level(:Test1, 1);

julia> AbstractAlgebra.set_verbosity_level(:Test2, 3);

julia> function v_do_example(a::Int, b::Int, c::Int, d::Int)
       @v_do :Test1 a = 2*a
       @v_do :Test2 2 b = 3*b
       @v_do :Test3 c = 4*c
       @v_do :Test2 4 d = 5*d
       return (a, b, c, d)
       end
v_do_example (generic function with 1 method)

julia> v_do_example(1,1,1,1)
(2, 3, 1, 1)
```

冗長性スコープを事前に設定しない場合、マクロは「Not a valid symbol」というエラーメッセージを表示する `ExceptionError` を発生させます。

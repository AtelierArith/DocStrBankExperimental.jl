```
@vprintln(S::Symbol, k::Int, msg::String)
@vprintln S k msg

@vprintln(S::Symbol, msg::String)
@vprintln S msg
```

このマクロは、コード内の印刷を制御するために使用できます。

マクロ `@vprintln` は、シンボル `S`（*冗長性スコープ*を指定）、オプションの整数 `k`、および文字列 `msg` の2つまたは3つの引数を取ります。`k` が指定されていない場合、デフォルトで $1$ に設定されます。

各冗長性スコープ `S` には、キャッシュされた *冗長性レベル* `l` が関連付けられています。`S` の冗長性レベル $l$ が `k` 以上である場合、マクロ `@vprintln` は関連する文字列 `msg` を改行付きで印刷します。

新しい冗長性スコープは、関数 [`add_verbosity_scope`](@ref) を呼び出すことで追加できます。

新しいインスタンスを開始すると、すべての冗長性レベルは $0$ に設定されます。冗長性スコープの冗長性レベルは、関数 [`set_verbosity_level`](@ref) を呼び出すことで調整できます。

冗長性スコープの現在の冗長性レベルには、関数 [`get_verbosity_level`](@ref) を呼び出すことでアクセスできます。

# 例

このマクロの使い方を示すために、異なる冗長性レベルを持つ異なる冗長性スコープをカスタム関数で設定します。

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:Test1);

julia> AbstractAlgebra.add_verbosity_scope(:Test2);

julia> AbstractAlgebra.add_verbosity_scope(:Test3);

julia> AbstractAlgebra.set_verbosity_level(:Test1, 1);

julia> AbstractAlgebra.set_verbosity_level(:Test2, 3);

julia> function vprint_example()
       @vprintln :Test1 "Triggered"
       @vprintln :Test2 2 "Triggered"
       @vprintln :Test3 "Not triggered"
       @vprintln :Test2 4 "Not triggered"
       end
vprint_example (generic function with 1 method)

julia> vprint_example()
Triggered
Triggered
```

事前に冗長性スコープを設定しない場合、マクロは「Not a valid symbol」というエラーメッセージを表示する `ExceptionError` を発生させます。

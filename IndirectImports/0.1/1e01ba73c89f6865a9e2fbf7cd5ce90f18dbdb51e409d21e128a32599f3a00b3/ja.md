```julia
@indirect function interface_function end
```

上流モジュール（すなわち、関数 `interface_function` を「所有する」モジュール）で `interface_function` を宣言します。この関数は、パッケージを定義することなく、下流パッケージで使用および/または拡張できます（`@indirect import Module` を介して）。この形式の `@indirect` は、トップレベルモジュールでのみ機能します。

```julia
@indirect function interface_function(...) ... end
```

上流モジュールで `interface_function` のメソッドを定義します。関数 `interface_function` は、上記の構文で最初に宣言されている必要があります。

これは、`@indirect import Module: interface_function` によって `interface_function` がインポートされている限り、下流モジュールでも使用できます（以下を参照）。

```julia
@indirect import Module
```

上流モジュール `Module` を間接的にインポートします。これにより、制限された方法でモジュールのように機能する定数 `Module` が定義されます。すなわち、`Module.f` を使用して関数 `f` を拡張または呼び出すことができます。ただし、実際のモジュール `Module` で `f` が「間接関数」として宣言されている必要があります（上記を参照）。

```julia
@indirect import Module: f1, f2, ..., fn
```

「間接関数」`f1`, `f2`, ..., `fn` をインポートします。これにより、拡張可能（上記を参照）で呼び出し可能な定数 `f1`, `f2`, ..., `fn` が定義されます。

```julia
@indirect function Module.interface_function(...) ... end
```

間接的にインポートされた関数のメソッドを定義します。この形式は、`Module` が `@indirect import Module` を介してインポートされている下流モジュールでのみ使用可能です。

# 例

`Downstream` パッケージで `Upstream` パッケージの関数を拡張したいとしますが、インポートせずに行います。

## ステップ 1: Upstream パッケージで間接関数を宣言する

間接関数の所有権を「宣言」するパッケージが必要です。通常、そのような関数は下流パッケージによって拡張されるインターフェースです。

パッケージ `Upstream` で関数 `fun` を宣言するには、空の関数定義 `function fun end` を `@indirect` でラップします。

```julia
module Upstream
    using IndirectImports
    @indirect function fun end
end
```

`Upstream` 内で間接関数のメソッドを定義するには、`@indirect` でラップします。

```julia
module Upstream
    using IndirectImports
    @indirect function fun end

    @indirect fun() = 0  # メソッドの定義
end
```

## ステップ 2: Downstream パッケージに上流パッケージを追加する

通常通り Pkg.jl インターフェースを使用して、`Downstream` パッケージの依存関係として `Upstream` パッケージを追加します。すなわち、`]add Upstream⏎` と入力します。

```julia-repl
(Downstream) pkg> add Upstream
```

これにより、`Project.toml` の `[deps]` に `Upstream` のエントリが追加されます。

```toml
[deps]
...
Upstream = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
...
```

デフォルトで `Upstream` をインストールするのが理想的でない場合は、`[extras]` セクションに移動します（手動で作成する必要があるかもしれません）。

```toml
[extras]
Upstream = "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
```

## ステップ 3: Downstream パッケージでメソッド定義を追加する

`Upstream` が `Project.toml` に登録されると、`Upstream` をインポートし、その関数を定義できます。ただし、`@indirect` マクロでプレフィックスを付ける必要があります。

```julia
module Downstream
    using IndirectImports
    @indirect import Upstream
    @indirect Upstream.fun(x) = x + 1
    @indirect function Upstream.fun(x, y)
        return x + y
    end
end
```

**注意**: メソッドの定義は、Julia の「バグ」により `@indirect` なしで機能するようです [^1]。デバッグやプロトタイピングなどのために `@indirect` なしでメソッドを定義するのは便利ですが、将来の Julia バージョンとの互換性を保つために、メソッド定義を `@indirect` でラップすることをお勧めします。

[^1]: コンストラクタの拡張は、`using` のみを使用して可能です [https://github.com/JuliaLang/julia/issues/25744](https://github.com/JuliaLang/julia/issues/25744)

# 制限

関数宣言は通常通り文書化できます。

```julia
"""
`fun` のドキュメント文字列。
"""
@indirect function fun end
```

しかし、メソッド定義では機能しません。

```julia
# 次のコメントアウトはエラーを引き起こします：

# """
# `fun` のドキュメント文字列。
# """
@indirect function fun()
end
```

下流パッケージの間接関数にドキュメント文字列を追加するための一つの回避策は、「オフサイト」ドキュメント文字列を使用することです。

```julia
@indirect function fun() ... end

"""
`fun` のドキュメント文字列。
"""
fun
```

# 仕組み

アイデアを理解するためのシンプルな自己完結型コードについては、[https://discourse.julialang.org/t/23526/38](https://discourse.julialang.org/t/23526/38) を参照してください。実際の実装は若干異なることに注意してください。

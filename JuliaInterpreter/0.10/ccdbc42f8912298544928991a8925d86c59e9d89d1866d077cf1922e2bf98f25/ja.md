```
ExprSplitter(mod::Module, ex::Expr; lnn=nothing)
```

モジュール `mod` と `mod` 内のトップレベル式 `ex` を与えると、評価のモジュールと共に個々の式を返すイテラブルを作成します。オプションで初期の `LineNumberNode` `lnn` を指定できます。

# 例

新しいセッションで、

```
julia> expr = quote
           public_fn(x::Integer) = true
           module Private
           private(y::String) = false
           end
           const threshold = 0.1
       end;

julia> for (mod, ex) in ExprSplitter(Main, expr)
           @show mod ex
       end
mod = Main
ex = quote
    #= REPL[7]:2 =#
    public_fn(x::Integer) = begin
            #= REPL[7]:2 =#
            true
        end
end
mod = Main.Private
ex = quote
    #= REPL[7]:4 =#
    private(y::String) = begin
            #= REPL[7]:4 =#
            false
        end
end
mod = Main
ex = :($(Expr(:toplevel, :(()), :(const threshold = 0.1))))
```

`ExprSplitter` は `Main.Private` を作成したので、その内部式を評価できるようになりました。`ExprSplitter` はモジュールがすでに存在するかどうかを確認し、存在する場合は新しいモジュールを作成しようとするのではなく、それを返します。

一般に、返される各式は2つの部分からなるブロックです：`LineNumberNode` の後に単一の式が続きます。返される式は、`const` 宣言に示されるように `:toplevel` である場合もありますが、そうでない場合は親の `head`（例：`expr.head`）を保持します。

# ワールドエイジ、フレーム作成、および評価

`ExprSplitter` の主な目的は、各式の評価後にトップレベル（例：REPL）に順次戻ることを可能にすることです。トップレベルに戻ることでワールドエイジが更新され、ブロック内の以前の式で定義されたメソッドや型を呼び出すことができるようになります。

JuliaInterpreter による評価のために、返されたモジュール/式のペアは `Frame` コンストラクタに直接渡すことができます。ただし、一部の式は `Frame` に変換できず、特別な処理が必要な場合があります：

```julia
julia> for (mod, ex) in ExprSplitter(Main, expr)
           if ex.head === :global
               # グローバル宣言は CodeInfo に降下できません。
               # このデモでは評価することを選択しますが、他のことをすることもできます。
               Core.eval(mod, ex)
               continue
           end
           frame = Frame(mod, ex)
           debug_command(frame, :c, true)
       end

julia> threshold
0.1

julia> public_fn(3)
true
```

パッケージコードを解析している場合、`ex` はドキュメント文字列式である可能性があります。そのような式をチェックし、異なるアクションを取ることを検討するかもしれません。

フレーム作成に関する詳細は [`Frame(mod::Module, ex::Expr)`](@ref) を参照してください。 ```

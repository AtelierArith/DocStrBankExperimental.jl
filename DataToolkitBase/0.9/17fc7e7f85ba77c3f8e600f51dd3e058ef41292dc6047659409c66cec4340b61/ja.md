```
Advice{func, context} <: Function
```

アドバイスは、関数呼び出しをカプセル化することによってデータの合成可能で非常に柔軟な修正を可能にします。これは、elispのアドバイスシステム、特に最も汎用的な形式である`:around`アドバイスとClojureのアドバイザーに触発されています。

`Advice`は本質的に関数ラッパーであり、`priority::Int`属性を持ちます。ラップされた関数は次の形式である必要があります：

```julia
(action::Function, args...; kargs...) ->
  ([post::Function], action::Function, args::Tuple, [kargs::NamedTuple])
```

`post`または`kargs`が省略された短縮形の戻り値も受け入れられ、その場合はデフォルト値（それぞれ`identity`関数と`(;)`）が自動的に代入されます。

```
    input=(action args kwargs)
         ┃                 ┏╸post=identity
       ╭─╂────advisor 1────╂─╮
       ╰─╂─────────────────╂─╯
       ╭─╂────advisor 2────╂─╮
       ╰─╂─────────────────╂─╯
       ╭─╂────advisor 3────╂─╮
       ╰─╂─────────────────╂─╯
         ┃                 ┃
         ▼                 ▽
action(args; kargs) ━━━━▶ post╺━━▶ result
```

どの変換に`Advice`を適用するかを指定するには、関連する型パラメータをトランスデューシング関数に追加してください。トランスデューシング関数が適用できない場合、`Advice`は単にアイデンティティ関数として機能します。

すべての適用可能な`Advice`が適用された後、`action(args...; kargs...) |> post`が呼び出されて最終結果が生成されます。

最終的な`post`関数は、アドバイス形式のすべての`post`エントリとの右方向合成によって作成されます（すなわち、各段階で`post = post ∘ extra`が実行されます）。

全体の動作は、アドバイスの*シェル*として考えることができます。

```
        ╭╌ advisor 1 ╌╌╌╌╌╌╌╌─╮
        ┆ ╭╌ advisor 2 ╌╌╌╌╌╮ ┆
        ┆ ┆                 ┆ ┆
input ━━┿━┿━━━▶ function ━━━┿━┿━━▶ result
        ┆ ╰╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╯ ┆
        ╰╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╌╯
```

# コンストラクタ

```julia
Advice(priority::Int, f::Function)
Advice(f::Function) # priorityは1に設定されます
```

# 例

**1. DataSetが読み込まれるたびにログを記録する。**

```julia
loggingadvisor = Advice(
    function(post::Function, f::typeof(load), loader::DataLoader, input, outtype)
        @info "Loading $(loader.data.name)"
        (post, f, (loader, input, outtype))
    end)
```

**2. 各データファイルの書き込みを自動的にコミットする。**

```julia
writecommitadvisor = Advice(
    function(post::Function, f::typeof(write), writer::DataWriter{:filesystem}, output, info)
        function writecommit(result)
            run(`git add $output`)
            run(`git commit -m "update $output"`)
            result
        end
        (post ∘ writecommit, writefn, (output, info))
    end)
```

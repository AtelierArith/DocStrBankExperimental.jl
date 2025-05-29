```
Term.jl
```

Term.jlへようこそ！Term.jlは、スタイル付きで美しいターミナル出力を生成するためのJuliaライブラリです。

# ドキュメント

ドキュメントについては、https://fedeclaudi.github.io/Term.jl を参照してください。

# デモ

```julia
using Term
const term_demo = joinpath(dirname(pathof(Term)), "..", "README.jl")
include(term_demo) # デモを表示
less(term_demo) # デモコードを見る
```

# 例

```julia

```

julia begin     println(@green "これは緑です")     println(@blue "そしてこれは青です")     println()     println(@bold "これは太字です")     println(@underline "そしてこれは下線付きです") end ```

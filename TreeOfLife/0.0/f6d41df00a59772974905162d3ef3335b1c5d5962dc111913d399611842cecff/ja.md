```
fromnewick(str::AbstractString; nocomments::Bool=false) :: AbstractTree
```

Newick形式のツリー文字列から系統樹を作成します。

その逆関数は[`tonewick`](@ref)です。

引数`nocomments`は、コメント（角括弧で囲まれた部分）を削除するかどうかを制御します。デフォルトでは`false`に設定されており、すべてのコメントが保持されます。

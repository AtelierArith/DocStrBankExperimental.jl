`ModuleElt{K,V}` は `Dict{K,V}` と似たインターフェースを持っていますが、`K` がハッシュ可能であることを前提とする代わりに、`K` がソート可能であることを前提としています。これにより、ModuleElt は自然にソート可能であるという利点もあります。

唯一のフィールドである `Vector{Pair{K,V}}` は `K` によってソートされた状態で保持されます。デフォルトでは、コンストラクタはソートをチェックし、同じキーを持つ値を追加し、ゼロ値のキーを削除します。これはキーワード `check=false` でオーバーライドできます。

列操作に対して高速なメモリレイアウトにタブローを変換します。

このレイアウトでは、タブローの列がメモリ内で（主に）連続して格納されます。ビットパッキング、例えば64ビットを単一の`UInt64`にパックすることにより、メモリレイアウトは完全に連続しているわけではありませんが、特定のビットを抽出するためにいくつかのビット操作が必要であるため、最適です。

参照: [`fastrow`](@ref)

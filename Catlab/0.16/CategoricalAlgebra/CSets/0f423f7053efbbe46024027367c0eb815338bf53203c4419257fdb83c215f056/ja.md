C-集合間の変換。

C-集合準同型は自然変換であることを思い出してください：これは、自然性公理を満たすC → Setの間の関手間の変換です。これは、C内のすべての射、または同等にすべての生成射に対して成り立ちます。

このデータ型はC-集合変換のデータを記録します。自然性は厳密には強制されませんが、満たされることが期待されます。これは、関数[`is_natural`](@ref)を使用してチェックできます。

domとcodomのスキーマに属性がある場合、これは組み合わせデータのみ（属性変数がある場合はそれも含む）に対して有効なC-集合変換であるという意味を持ちます。
